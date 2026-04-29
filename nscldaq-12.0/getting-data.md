|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 72. Support for CAEN Nextgen DPP-PHA digitizers | Next |


---

# <a name="ch.readout"></a>72.2. Getting Data

Data is read from modules using a tailored SBS readout program that
            makes use of classes that have been written to support the new
            CAEN VXxxxx digitizers and DPP-PHA firmware.   These modules have
            a huge number of settable parameters.

To manage the settable parameters, each module is associated with a
            *configuration*.  The module's configuration
            captures the desired settings for that module.  A module is assigned
            a name by your software and a matching named configuration is  read
            and used to configure that module at the start of each run.  The
            configuration is re-read each begin run so that changes can be made
            between runs.

[[x15738#sec.rdoprogramming]]
            describe how to tailor an SBS readout skeleton to produce a readout
            program.   [[x15738#sec.rdoconfig]]
            describes how to create module configurations and the parameters
            that can be set for a module.

A few notes:



- While the software was developed with 12.0-pre, I believe the
                    support software will function with 11.3 as well.
- Since each module is assigned a source id, when event building
                    the readout program should be run with the
                    `--no-barriers` optioon in order to prevent
                    the event builder from stalling on a barrier wait at the start
                    and end of runs.

## <a name="sec.rdoprogramming"></a>72.2.1. Obtaining and modifying the skeleton

The Readout is based on the SBS readout skeleton.  This
                software allows for an experiment specific trigger which causes
                experiment specific code to be run.  SBS readout skeletons, therefore
                require tailoring to fit specific applications.

Here are the steps required to tailor that system for the
                CAEN modules:



1. Select the version of NSCLDAQ you will use, and source in its
                         setup file to define environment variables that will make
                         your life easier.
2. Obtain a copy of the sbs skeleton in an emtpy directory.
3. Make appropriate modifications to the
                         Skeleton.cpp's
                         `Skeleton::SetupReadout` method
                         to define the modules you will be using.
4. Modify the Makefile provided with the skeleton to pull in the
                         libraries and headers that make up support.
5. Build the Readout program.
6. Write a configuration file that appropriately configures
                         each module you defined (covered in
                         [[x15738#sec.rdoconfig]]).

The remainder of this section assumes you have selected
                NSCLDAQ-12.0-pre5.    To obtain that skeleton:

<a name="AEN15774"></a>**Example 72-1. 
                    Selecting DAQ version and obtaining the skeleton:
                **

```

source /usr/opt/daq/12.0-pre5/daqsetup.bash
mkdir myreadout
cd myreadout
cp $DAQROOT/skeletons/sbs/* .

                
```

### <a name="AEN15777"></a>72.2.1.1. Modifying the Skeleton

In this example, the key class is:
                    `TclConfiguredReadout` is a container
                    class that is an *CEventSegement* that
                    holds a set of modules to readout and constructs and appropriate
                    trigger to drive the readout.  It will also construct
                    and maintain objects for each module.

Construction specifies a configuration file that is processed
                    at the beginning of each run and used to program the
                    configuration of each module.

The class's `addModule` method
                    creates a module driver for a module, providing the connection
                    parameters for that module and associating it with a module
                    configuration within the configuration file. Each module,
                    so defined must be assigned a source id that is unique
                    across the system.  This source Id is used in event building.

Here are the parameter signatures for the methods you need
                    to use:



`  TclConfiguredReadout(const char* configfile, CExperiment* pExperiment);`Constructor.  `configfile` is the
                            path to a file that describes configurations for each
                            module that will be added to this event segment
                            (see `addModule`).

` void addModule(const char* name, const char* connectionString, std::uint32_t sid, bool isusb = false);`Adds a module to the readout.  `name`
                                is the name of a module in the configuration
                                file specified in the construtor.

`connectionString` is a string
                            that describes how the module is connected to the system.
                            This string is either a dotted IP address (e.g
                            "127.0.0.1") if ETHERNET is used or the PID of the module
                            if USB is used.  Note that DNS lookups are not done for
                            host names but there is nothing to stop you from doing
                            host lookups yourself prior to calling
                            `addModule`

`sid` is a unique integer source id
                            that identifies this module to the event builder.

`isUsb` is an optional parameter
                            that defaults to false.
                            If true, it specifies that the
                            `connectionString` is a module PID
                            and that the connection is via USB.

` CTrigger* getTrigger();`Returns a pointer to the trigger that the object
                            has computed for the modules that have been added to it.
                            This should be used to supply a trigger object to the
                            Readout program framework.

Let's look at a simple example.  The full example is in
                    the tclreadout subdirectory of the
                    source tree.  If you want to use that as a starting point,
                    simply modify the INSTDIR definition
                    at the top of the file to point to the version of NSCLDAQ
                    you decided to use.

<a name="ex.skeleton"></a>**Example 72-2. Sample Skeleton.cpp modifications**

```
#include <config.h>
#include <Skeleton.h>
#include <CExperiment.h>
#include <TCLInterpreter.h>
#include <CTimedTrigger.h>
#include <TclConfiguredReadout.h>   
#include <Dig2Device.h>             

using namespace caen_nscldaq;
...

void
Skeleton::SetupReadout(CExperiment* pExperiment)
{
 
  CReadoutMain::SetupReadout(pExperiment);
  
  // turns on felib tracing if compiled with it enabled

  // caen_nscldaq::set_tracing(true);    
  
  // First we create a TclConfiguredReadout object and describe the
  // connections to the modules in the system -- assigning each
  // module a distinct source id for event building.
  // Note that the event builder allows fragments from the same source to get
  // grouped into the same event and each fragment is tagged with its channel..
  // so per-module sids rather than per-channel work just fine:
  
  auto pSegment = new TclConfiguredReadout(   
    "configuration.tcl",            // Detailed module settings file path.
    pExperiment                     // Pointer to experiment object.
  );
  pSegment->addModule(                    
    "adc1",                   // Name of module in configuration.tcl
    "15236",                   // PID for USB connection, IP If ethernet.
    1,                        // System unique source id.
    true                      // Indicates it's USB not Ethernet defaults to false.
  );
  
  pExperiment->AddEventSegment(pSegment);   
  
  // The event segment creates a dynamic multi trigger object which we need
  // to fetch out and register as the trigger for the system:
  
  pExperiment->EstablishTrigger(pSegment->getTrigger()); 
  
}


                    
```

[[x15738#rdo.classinc]]                            This #include is needed to define
                            the `TclConfiguredReadout`
                            class.
                        [[x15738#rdo.tracinginc]]                            Wrappers for the CAEN libraries support tracing the
                            operations and responses performed on the module.
                            This header provides definitions needed to enable
                            this tracing.  Note that tracing must be enabled both
                            programmatically and via a compilation option in the
                            library Makefile.
                        [[x15738#rdo.tracing]]                            If the library has been built with tracing enabled,
                            uncommenting this line will turn that on. Note that this
                            will create a large trace file, as well as adversely
                            impact performance.
                        [[x15738#rdo.makesegment]]                            Creates the `TclConfiguredReadout`
                            object that will manage the modules we will use.
                            At the start of each run, configuration.tcl
                            will be processed to load the configuration for each
                            module and each module will then be asked to configure itself
                            in accordance with its configuration.  The
                            `pExperiment` pointer passed in
                            to `SetupReadout` points to
                            an object that provides services needed.
                        Note that `SetupReadout` is only
                            called once at system startup and the lifetime of the
                            `TclConfiguredReadout` will be
                            the lifetime of the Readout program.  Therefore,
                            the fact that the `pSegment`
                            never is deleted is not a memory leak.

[[x15738#rdo.addmodule]]                            Adds a module to the system.  The module is named
                            adc1 and will, therefore expect
                            a configuration for adc1.
                            It is a USB connected module with PID 
                            15236 and is assigned source id
                            1.
                        The `TclConfiguredReadout`
                            will manage this module from now on.  It will also
                            produce a part of the readout trigger based
                            on data being available in this module.

[[x15738#rdo.registersegment]]                            The `TclConfiguredReadout`
                            event segment is registered with the experiment framework
                            so that its methods will be invoked by that framework
                            when appropriate.
                        [[x15738#rdo.registertrigger]]                            The trigger computed by the
                            `TclConfiguredReadout` event
                            segment is fetched and established as the trigger
                            for readout.  When a run is active this trigger is
                            polled and, when it indicates that it has been
                            triggered, readout will ensue.

### <a name="AEN15886"></a>72.2.1.2. Modifying the Makefile and Building Readout

The CAEN digitizer support software (NSCLDAQ and base).  The
                    SBS skeleton readout Makefile must be edited to ensure that
                    appropriate include directories are searched when compiling
                    and libraries pulled in when linked.  The example below shows
                    the bits of the Makefile that are needed to arrive at proper
                    definitions of
                    USERCCFLAGS and
                    USERLDFLAGS, the additional
                    options given at compile and link time.

<a name="AEN15891"></a>**Example 72-3. Front part of Makefile for Readout**

```
INSTDIR=/usr/opt/daq/12.0-pre3

include $(INSTDIR)/etc/SBSRdoMakeIncludes

FELIB_CPPFLAGS=
FELIB_LDFLAGS=-lCAEN_FELib



JSON_CPPFLAGS = $(shell pkg-config jsoncpp --cflags)
JSON_LDFLAGS  = $(shell pkg-config jsoncpp  --libs)

#Where the support softare was installed.
# starting with NSCLDAQ-12.1, support software is installed 
# in NSCLDAQ
NSCL_SUPPORT_PREFIX=$(INSTDIR)

#
#  The following allow you to add flags to all the default C and C++ compilation
#  rules.  In most cases C and C++ share the same set of compilation flags so:
#
#

USERCCFLAGS= -I$(NSCL_SUPPORT_PREFIX)/include $(JSON_CPPFLAGS) $(FELIB_CPPFLAGS)
USERCXXFLAGS=$(USERCCFLAGS)

#  If you have additional load flags (e.g. library dirs and libs):

USERLDFLAGS=-L$(NSCL_SUPPORT_PREFIX)/lib -lCaenVx2750 \
        $(JSON_LDFLAGS) $(FELIB_LDFLAGS) \
        -lboost_log -lboost_log_setup  -lboost_thread -lboost_system -lcrypto


                    
```

Note that the INSTDIR definition should
                    point to the version of NSCLDAQ being used and
                    NSCL_SUPPORT should point to where the
                    CAEN nextgen digitizer support librariers are installed.
                    The boost libraries are used to support logging digitizer
                    requests if enabled for debugging while the crypto library
                    pulls in code to compute MD5 digests

An important note about MD5 digests.  The digitizer is
                    only fully initialized on the first begin run after Readout
                    starts or when the MD5 digest of the configuration files
                    changes (implying the configuration file itself changed).
                    This is done because a complete initialization of a module
                    takes a significant amount of time.

The use of MD5 digests, improves run start time as the configuration
                    of the digitizers becomes stable and the configuration file
                    is no longer being routinely edited. *However*,
                    if the digitizers are powered off between runs, this is not
                    detectable by the system and initialization will
                    *not* be performed unless either
                    the configuration file is edited (e.g. adding a comment),
                    or the Readout program restarted.

Once the Makefile has been appropriately edited, the Readout program can be built
                    via **make**

## <a name="sec.rdoconfig"></a>72.2.2. Configuring modules

Each module must be configured to be useful.  This is done by
                writing a configuration script.  Configuration scripts are
                written in a domain specific language layered on top of the
                Tcl scripting language.  Tcl is extended by adding a single command
                ensemble: **v27xxpha** to Tcl.

A command ensemble in Tcl parlance is a single command that has
                subcommands specified by the next word on the command line.  The
                **v27xxpha** command has the following forms:



**vx27xxpha create *module-name***Creates a new configuration for a module `module-name`.
                        When the Readout initializes modules it looks for configurations
                        that match the names of modules that have been added
                        to the `TclConfiguredReadout`
                        module.

thus in our example
                        [[x15738#ex.skeleton]]
**vx27xxpha create adc1** would create
                         a configuration for the module we added.

**vx27xxpha config *module-name name value ...***Configures one or more parameter values for the
                        `module-name`.  Any number of
                        parameter name/value pairs can be specified on the command.
                        For example:
                        **v27xxpha config adc1 dcoffsets [lrepeat 64 0]**
                        Configures the DC offsets for all 64 channels to be 0% of
                        full scale.

**vx27xxpha cget *module-name name***This command returns the value of the parameter
                        `name` from the configuration
                        for the module `module-name`.
                        For example:
                        **puts [vx27xxpha cget adc1 dcoffsets]**
                        will print 64 zeroes to stdout.

**vx27xxpha delete *module-name***Really not necessary - this deletes the configuration
                        for `module-name`.  Since the
                        configuration file is processed and all configuration rebuilt
                        from scratch at each begin run,
                        there's really no need to delete modules.

**vx25x0 list**Returns a list of the module names that have configurations.
                        the following little script will list the modules
                        configured, one per line to stdout:

<a name="AEN15950"></a>```
foreach module [vx27xxpha list] {
    puts $module
}
                        
```

A sample configuration file that goes along with the
                sample readout program in the tclreadout
                subdirectory of the source tree is 
                /configuration.tcl.

### <a name="AEN15955"></a>72.2.2.1. Configuration parameter reference

This section consists of several subsections.  Each
                    subsection provides a reference for a set of configuration
                    parameters that are related in some way.
                    Parameters are describes as follows:

****

**Name: **Name of the parameter

**Data type: **Data type the item must be

**Default: **Defeault value for the item

**Description: **Description of the item.

A note on the boolean data type.  Any of the following are
                    valid true values:
                    true, yes, 1, on, enabled, while any
                    of the following are valid false value
                    false, no, 0, off, disabled.

A note on integer data types.  These can be expressed in base
                    10, 16 or 8. Base 16 values should be prefixed by 0x,
                    e.g. 0x5a5a5a5a5a5a5a5a.  Base 8 values
                    are prefixed by a leading zero e.g. 0777.

|  |  |
| --- | --- |
|  | WARNING |
|  | Do not use leading zeros to align decimal values,
                        they will be treated as octal and, in general,
                        not have the intended effect.  This is a curse that has
                        afflicted many a user of the Tcl language. |

When in doubt about the meaning of a parameter see CAEN
                    document
                    UM7788 --FELib PHA Parameters User Manual.

#### <a name="AEN15979"></a>72.2.2.1.1. Readout Options

The parameters in this section are not actually digitizer
                        parameters, the determine what is read from the
                        digitizer at each event.  All events will read the
                        event channel number, timestamp in nanosecods
                        and energy from the DPP-PHA.
                        These options allow additional available parameters/features
                        to be read from the digitizer.

The configuration parameters are:

****

**Name: **readrawtimes

**Data type: **boolean

**Default: **false

**Description: **If enabled, the raw time stamp counter is included
                        in each event.  Note that the nanosecond timestamp
                        is always used for even building as the raw timestamp
                        may vary in frequency depending on the digitizer.

**Name: **readfinetimestamps

**Data type: **boolean

**Default: **false

**Description: **If enabled, and if the module supports the generation
                        of fine timing information (e.g. interpolated timing from
                        a CFD), turning this on enables the inclusion of that fine
                        timing information in the event.

**Name: **readflags

**Data type: **boolean

**Default: **false

**Description: **If enabled reads various bits that report on the
                        digitizer's state

**Name: **readtimedownsampling

**Data type: **boolean

**Default: **false

**Description: **If enabled, reads a code that corresponds to the
                        digitizer sampling scaledown

**Name: **readanalogprobes

**Data type: **list of two booleans

**Default: **{false false}

**Description: **The module supports two analog probes these can be used
                        to acquire the input waveforms as well as various diagnostic
                        information.  The first element of the list enables/disables
                        the inclusion of analog probe1 and the second the inclusion of
                        analog probe 2

**Name: **readdigitalprobes

**Data type: **list of four booleans

**Default: **{false false false false}

**Description: **The digitizer supports the inclusion of four digital probes.
                        A digital probe has a byte per sample with a value of 0 or
                        1.  The list can selectively enable the inclusion of data
                        from each probe.

**Name: **readsamplecount

**Data type: **boolean

**Default: **false

**Description: **If enabled, the number of samples read for this
                        channel are included.

**Name: **readeventsize

**Data type: **boolean

**Default: **false

**Description: **If enabled, the raw event size is read.

#### <a name="AEN16029"></a>72.2.2.1.2. General options

These parameters control general module wide functionality.

****

**Name: **clocksource

**Data type: **Enumerated

**Default: **Internal

**Description: **Selects the source of the digitizer's clock.
                        Valid values are Internal
                        to use the module's internal clock or
                        FPClkIn to use the front panel clock
                         input.

**Name: **outputfpclock

**Data type: **boolean

**Default: **false

**Description: **If true, the digitizer clock is output
                        on the front panel.  This allows modules to use a single
                        shared clock source without needed an external clock.
                        Clock delays can then compensate for clock propagation
                        delays as one progresses  down the clock in/clock out
                        daisy chain.

#### <a name="AEN16052"></a>72.2.2.1.3. Triggerring and I/O

The parameters control digitizer and channel level triggers
                        as well as the LEMO connectors on the front panel.

****

**Name: **startsource

**Data type: **List of enumerated values

**Default: **SWcmd

**Description: **The list of ways the digitizer can start a run.
                        The digitzer is started on the or of the conditions
                        in the list.  Usually, in a synchronized set, the
                        'master' digitizer is stated on SWcmd and the others
                        on e.g. SINedge.   Valid values for list elements are:
                        EncodedClkIn, SINlevel, SINedge, SWcmd, LVDS, P0

**Name: **gbltriggrsrc

**Data type: **List of Enums

**Default: **TrgIn

**Description: **The sources of the module global trigger.  The
                        or of the values listed makes a global trigger.
                        Valid values are
                        TrgIn, P0, SwTrg, LVDS, ITLA, ITLB,
                        ITLA_AND_ITLB, ITLA_OR_ITLB, EncodedClkIn, GPIO,
                        TestPulse

**Name: **wavetriggersrc

**Data type: **List of 64 lists of enums

**Default: **[lrepeat TRGIN 64]

**Description: **This parameter is a list of 64 trigger sources for
                        wave acquisition.  Each element of that list is itself
                        a list of triggers sources for that channel.  Valid
                        values for the trigger sources are:
                                                    ITLB, ITLA, GlobalTriggerSource, TRGIN, ExternalInhibit,
                            ADCUnderSaturation, ADCOverSaturation, SWTrg, ChSelfTrigger,
                            Ch64Trigger, Disabled

**Name: **eventtriggersrc

**Data type: **List of 64 lists of enums

**Default: **[lrepeat TRGIN 64]

**Description: **Similar to the wavetriggersrc
                        but provides, for each channel a list of event trigger
                        sources.   Valid values are:
                                                    ITLB, ITLA, GlobalTriggerSource, TRGIN, SWTrg, ChSelfTrigger,
                            Ch64Trigger, Disabled

**Name: **channeltriggermasks

**Data type: **List of 64 uint64_t

**Default: **[lrepeat 0 64]

**Description: **In Ch64Trigger mode, or coincidence
                        triggering mode, used to define the set of channels that
                        particpate in triggering each channel.

**Name: **savetraces

**Data type: **List of 64 enums

**Default: **[lrepeat OnRequest 64]

**Description: **Determines when wave traces are saved for each
                        channel.  Valid values are
                        Always, OnRequest

**Name: **triggeroutmode

**Data type: **Enumerated value

**Default: **TRGIN

**Description: **Determines what is output on the TRGOUT
                        LEMO output.  Valid values are:
                                                    TRGIN, P0, SwTrg, LVDS, ITLA, ITLB,
                            ITLA_AND_ITLB, ITLA_OR_ITLB, EncodedClkIn,
                            Run, RefClk, TestPulse,
                            Busy, Fixed0, Fixed1, SyncIn, SIN, GPIO,
                            AcceptTrg, TrgClk

**Name: **gpiomode

**Data type: **Enumerated value

**Default: **Disabled

**Description: **Selects the signal to output on the
                        GIO LEMO connector.
                        This can be one of
                                                    Disabled, TrgIn, P0, SIN, LVDS, ITLA, ITLB,
                            ITLA_AND_ITLB, ITLA_OR_ITLB, EncodedClkIn, SwTrg,
                            Run, RefClk, TestPulse, Busy, Fixed0, Fixed1

**Name: **busyinsrc

**Data type: **Enumerated value

**Default: **Disabled

**Description: **Determines the source of the external
                        module busy input.  This is one of:
                        SIN, GPIO, LVDS, Disabled

**Name: **syncoutmode

**Data type: **Enumerated value

**Default: **Disabled

**Description: **
                            Determines the source of the SOUT
                            LEMO connector.  Valid values are
                                                            Disabled, SyncIn, TestPulse, IntClk, Run

**Name: **boardvetosrc

**Data type: **Enumerated value

**Default: **Source of the board level trigger veto. Valid values are
                                                    SIN, LVDS, GPIO, P0, EncodedClkIn, Disabled

**Name: **boardvetowidth

**Data type: **Integer nano-seconds 0 - 34359738360

**Default: **200

**Description: **Ns stretch applied to the board veto source

**Name: **boardvetopolarity

**Data type: **Enumerated value

**Default: **ActiveLow

**Description: **
                            Polarity of the veto input.  One of
                            ActiveHigh, ActiveLow

**Name: **chanvetosrc

**Data type: **list of 64 enumerated values

**Default: **[lrepeat Disabled 64]

**Description: **Veto sources for each of the channels.  Each list element
                        can have one of the value:
                                                    BoardVeto, ADCOverSaturation, ADCUnderSaturation, Disabled

**Name: **chanvetowidth

**Data type: **List of 64 integer in units of ns 0-524280

**Default: **[list 200 64]

**Description: **The stretch applied to each channel's veto source.

**Name: **rundelay

**Data type: **Integer nanoseconds 0-54280

**Default: **0

**Description: **
                            This value is used to fine tune the synchronized
                            start of multi-board data taking. When the start source
                            is true, the actual start will be delayed by the ns
                            set in this parameter.  If, for example, the start is
                            propagated via a SIN/SOUT daisy chain on the front panel, the
                            final board will be delayed by 0 ns, the next to last
                            board by the single board propagation delay and so on.

**Name: **chanvetowidth

**Data type: **boolean

**Default: **true

**Description: **When true, the module is disarmed when data taking is
                        stopped.

**Name: **volclkoutdelay

**Data type: **Floating point ps -18888.8888 - 18888.8888

**Default: **0.0

**Description: **
                            Sets the value that is programmed into the clock PLL
                            delay.  This is used to synchronize clocks passed between
                            boards via the CLKOUT/CLKIN daisy chain.

**Name: **permclkoutdelay

**Data type: **volclkoutdelay

**Default: **Floating point ps -18888.8888 - 18888.8888

**Description: **0.0

**: **
                            Sets the value that is programmed into the clock PLL
                            delay on power up.  This is used to synchronize clocks passed between
                            boards via the CLKOUT/CLKIN daisy chain.  Note that
                            this value is first programmed and then the volclkoutdelay
                            which actually controls the clock delay.
                            In a future bit of development a parameter migth be
                            added to select which of these two values controls
                            the actual clock delay.

#### <a name="AEN16174"></a>72.2.2.1.4. Wave form inspection and digital probes.

Note that whlie the waveform and digital probe values are
                        programmed here, in order to actually include those
                        probes in the data read from the digitizer,
                        readanalogprobes and/or
                        readdigitalprobes must be set
                        accordingly.

****

**Data type: **wavesource

**Default: **List of enumerated values

**Description: **[lrepeat ADC_DATA 64]

**: **
                            This is a list of one entry per channel that describes
                            what the FADC for that channel sees on its input.
                            Valid values are:
                                                            ADC_DATA, ADC_TEST_TOGGLE, ADC_TEST_RAMP,
                                ADC_TEST_SIN, IPE,
                                 Ramp, SquareWave, ADC_TEST_PRBS

**Data type: **recordsamples

**Default: **List of 64 integers 4-8100

**Description: **[lrepeat 4 64]

**: **Each element determines the number of samples that
                        channel of the ADC will process/record.  The actual time
                        represented depends on the value of the saveresolutions
                        parameter for that channel.

**Data type: **waveresolutions

**Default: **list of 64 enumerated values

**Description: **[lrepeat Res8 64]

**: **For each channel, selects the sampling resolution in
                        nanoseconds.

**Data type: **analogprobe1, analogprobe2

**Default: **List of 64 enumerated values

**Description: **[lrepeat ADCInput 64], [lrepeat TimeFilter 64]

**: **
                            For each channel, the analog probes available
                            for acquisition from that channel.   Allowed values
                            are:
                                                            ADCInput, TimeFilter, EnergyFilter,
                                EnergyFilterBaseline,
                                EnergyFilterMinusBaseline

**Data type: **digitalprobe1, digitalprobe2, digitalprobe3, digitalprobe4

**Default: **list of 64 enumerated values

**Description: **[lrepeat Trigger 64], [lrepeat TimeFilterArmed 64],
                        [lrepeat RetriggerGuard 64],
                        [lrepeat EneryFilterBaselineFreeze 64]

**: **
                            For each channel, the digital probes available for
                            acquisition from that channel.  Valid values are:
                                                            Trigger, TimeFilterArmed, ReTriggerGuard,
                                EnergyFilterBaselineFreeze,
                                EnergyFilterPeaking, EnergyFilterPeakReady,
                                EnergyFilterPileUpGuard, EventPileup, ADCSaturation,
                                ADCSaturationProtection, PostSaturationEvent,
                                EnergyFilterSaturation,
                                AcquisitionInhibit

**Data type: **pretriggersamples

**Default: **List of 64 integers 4-4000

**Description: **[lrepeat 100 64]

**: **For each channel, the number of samples
                        prior to the trigger that will be acquired and
                        analyzed by the DPP-PHA firmware.

#### <a name="AEN16218"></a>72.2.2.1.5. Service options

These, for the most part, have to do with the test pulser.
                        There are also miscellaneous parameters to control
                        error handling and the LEMO I/O levels.

****

**Name: **testpulserperiod

**Data type: **Integer ns 0-34359738360

**Default: **100000

**Description: **The period of the test puler in ns.

**Name: **testpulsewidth

**Data type: **Integer ns 0-34359738360

**Default: **1000

**Description: **Width of the high part of the test pulser
                        period.

**Name: **testpulselowlevel

**Data type: **Integer 0-65535

**Default: **0

**Description: **The low level output of the pulser

**Name: **testpulsehighlevel

**Data type: ** Integer 0-65535

**Default: **65535

**Description: **The high level output of the pulser

**Name: **iolevel

**Data type: **Enumerated value

**Default: **NIM

**Description: **The signalling level to be used by the
                        LEMO I/O connectors.  This can be one of
                        NIM or TTL

**Name: **errorflagmask

**Data type: **Integer 0-0xffff

**Default: **0

**Description: **Error flag bitmask that determines what lights
                        the front panel error LED given specific error
                        conditions

**Name: **errorflagdatamask

**Data type: **Integer  0-0xffff

**Default: **0

**Description: **Error flag bitmask that determines which which error
                        conditions result in an error condition in the event.

#### <a name="AEN16264"></a>72.2.2.1.6. Internal Logic block parameters

Triggers can be the result of sophisiticated conditions in
                        two internal logic blocks called ITLA and ITLB.
                        This set of parameters determine how those  logic blocks
                        function.  Because there are two logic blocks, These
                        parameters are  mostly in pairs, on parameter for ITLA
                        and a second for ITLB

** **

**Name: **itlalogic, itlblogic

**Data type: **Enumerated value

**Default: **OR, OR

**Description: **
                            Determines how the channel inputs to the
                            ITLA/ITLB logic blocks are interpreted to
                            create a trigger output from that block.
                            Options are:
                                                          OR, AND, Majority
                            
                            Note that if Majority  is selected,
                            itlxmarjoritylevel determines the
                            actual majoriy level required.

**Name: **itlamajoritylevel, itlbmajoritylevel

**Data type: **Integeer 1-63

**Default: **1

**Description: **The majority level for the specified trigger
                        gropu.  Note this is only relevant if the corresponding
                        trigger block is functioning in Majority
                        mode.

**Name: **itlapairlogic, itlbparilogic

**Data type: **Enumerated value

**Default: **None, None

**Description: **
                            Adjacent channel pairs (0,1 2,3 etc.) can be combined
                            as inputs to the ITLA or ITLB logic blocks. These
                            parameters determine if and how those pairs are combined.
                            When combined, both outputs of the pair will be the
                            ouptput of the logic function applied (e.g. if in AND
                            mode and only channel 0 triggers, then both inputs 0 and 1
                            will be in the untriggered state as inputs to the logic block).
                            Possible values are:
                                                            AND, OR, NONE
                              Where AND as well as
                            OR combine the inputs into a paired
                            while NONE passes the inputs to their
                            corresonding outputs without any pair logic.

**Name: **itlapolarity, itlbpolarity

**Data type: **Enumerated value

**Default: **Direct, Direct

**Description: **Determines the output polarity of the specified
                        trigger logic block.
                        This can be either Direct
                        or Inverted

**Name: **itlamask, itlbmask

**Data type: **Integer 0 - 0xffffffffffffffff

**Default: **0xffffffffffffffff, 0xffffffffffffffff

**Description: **This mask has a bit for each channel, if set that channel
                        participates in the associated internal trigger logic block.

**Name: **itlagatewidth, itlbgatewidth

**Data type: **Integer nanoseconds 0-524280

**Default: **100, 100

**Description: **The ITLA and ITLB outputs are inputs to gate generators.
                        These parameters determine the width of the output of that
                        gate generator in ns.

#### <a name="AEN16313"></a>72.2.2.1.7. LVDS Options

The 16 LVDS I/Os can be programmed in a sets of four (quartets).
                        The parameters in this section describe how to configure them.

****

**Name: **lvdsmode

**Data type: **List of 4 enumerated values

**Default: **[lrepeat IORegister 4]

**Description: **
                                Determines the functionality of each of the four
                                quartets of LVDS I/Os:
                                SelfTriggers, Sync, IORegister.

**Name: **lvdsdirection

**Data type: **List of four enumerate valus

**Default: **[lrepeat Output 4]

**Description: **Determines the direction of each of the four
                            quartests of LVDS I/Os: Input, Output

**Name: **lvdstrgmask

**Data type: **List of 16 integer values 0 - 0xffffffffffffffff

**Default: **[lrepeate 0 16]

**Description: **If a quartet is in SelfTriggers
                            mode as an Output, these masks
                            determine which self triggers are associated with each pin
                            of the LVDS output in that quartet.  There are 16 elements
                            corresponding to each of the 16 LVDS I/O pins. If
                            a pin is not in a quartet that is configured as
                            a SelfTriggers Output
                            it's mask is ignored.

**Name: **lvdsoutput

**Data type: **Integer 0-0xffff

**Default: **0

**Description: **
                                If a pin is part of a quartet that's configured for
                                IORegister, Output,
                                The corresponding bit of this mask determines the
                                value of that pin.

#### <a name="AEN16350"></a>72.2.2.1.8. DAC  options

Each module has a dedicated Digital to Analog Converter
                        (DAC).  The DAC LEMO output on the
                        module front panel reflects the output of this device.
                        These parameters control what that is.

****

**Name: **dacoutmode

**Data type: **Enumerated Value

**Default: **ChSum

**Description: **Determines what the input to the DAC is.
                            Legal values are
                                                            Static, IPE, ChInput, MemOccupancy, ChSum, OverThrSum,
                                Ramp, Sin5MHz, Square

**Name: **dacoutputlevel

**Data type: **Integer 0-16383

**Default: **0

**Description: **
                                If the output mode is Static,
                                the output is the DAC conversion of this value
                                as its input.

**Name: **dacoutchannel

**Data type: **integer 0-63

**Default: **0

**Description: **If the DAC output mode is
                            ChInput this value selects the
                            channel input that is echoed on the DAC output.

#### <a name="AEN16378"></a>72.2.2.1.9. Input conditioning

Describes the parameters that control the relationship
                        between the raw ADC inputs and what the digitizers see.

****

**Name: **vgagain

**Data type: **List of four integers 0-40

**Default: **0

**Description: **If the module is equipped with variable gain
                            amplifiers on its input, each amplifier gain is common
                            between 16 inputs.  This list of parameters sets the
                            VGA Gain for groups of 16 channels.

**Name: **offsetcalibrationenable

**Data type: **Boolean value

**Default: **true

**Description: **Enable/disable the offset calibraion for each channel.

**Name: **channelenables

**Data type: **List of 64 booleans

**Default: **[lrepeat true 64]

**Description: **
                                For each channel when its corresponding list element
                                is true, the channel is enabled, otherwise it is
                                disabled.

**Name: **dcoffsets

**Data type: **List of 64 floats 0-100.0

**Default: **[lrepeat 50.0 64]

**Description: **For each channel, this is the DC Offset applied
                            to the channels.

**Name: **triggerthresholds

**Data type: **64 element list of integers 0-8191

**Default: **1023

**Description: **
                                Channel trigger thresholds.

**Name: **inputpolarities

**Data type: **list of 64 enums

**Default: **[lrepeat Negative 64]

**Description: **Sets the polarity of the input pulse for each channel.
                            Valid values are Positive
                            and Negative

#### <a name="AEN16419"></a>72.2.2.1.10. Event Selection Options

The module has several post trigger event filtering options
                        that can be set.  These options are exposed as:

****

**Name: **energyskimlow

**Data type: **64 element integer list 0-65534

**Default: **[lrepeat 0 64]

**Description: **
                                Events in a channel with computed energies
                                less than this value (for that channel) are not
                                passed to the host.

**Name: **energyskimhigh

**Data type: **64 element integer list 0-65534

**Default: **[lrepeat 65534 64]

**Description: **
                                Events in a channel with computed energies
                                higher than this value (for that channel) are not
                                passed to the host. Thus the energyskimlow
                                and energyfilterhigh values
                                for each channel provide an energy cut between
                                which events are accepted and outside of which
                                they are rejected.  See, however
                                eventselector

**Name: **eventselector

**Data type: **List of 64 enumerated values

**Default: **[lrepeat All 64

**Description: **
                                Selects which events (energy values) are
                                saved for each channel. Valid values for each
                                element of the list are
                                All, Pileup, EnergySkim.

**Name: **waveselector

**Data type: **List of 64 enumerated values

**Default: **[lrepeat All 64

**Description: **
                                Selects which waveforms are
                                saved for each channel. Valid values for each
                                element of the list are
                                All, Pileup, EnergySkim.

**Name: **coincidencemask

**Data type: **List of 64 enumerated values

**Default: **[lrepeat Disabled 64]

**Description: **
                                Defines a concidence source for a trigger on each
                                channel.  Valid values are:
                                                                    Disabled, Ch64Trigger, TRGIN,
                                    GlobalTriggerSource, ITLA, ITLB

**Name: **anticoincidencemask

**Data type: **List of 64 enumerated values

**Default: **[lrepeate Disabled 64

**Description: **
                                Defines an anticoincidence source for a trigger
                                on each channel.  Valid values are:
                                                                    Disabled, Ch64Trigger, TRGIN,
                                    GlobalTriggerSource, ITLA, ITLB

**Name: **coincidencelength

**Data type: **List of 64 integer values in nanoseconds 8-524280

**Default: **[lrepeat 100 64

**Description: **
                                Defines, for each channel, the coincidence window
                                in nanoseconds for the coincidence and anti
                                coincidence trigger sources defined by
                                coincidencemask
                                and anticoincidencemask.

#### <a name="AEN16472"></a>72.2.2.1.11. DPP Processing parameters

Firmware on the module processes raw, digitized wave forms
                        into pulse heights (energies).  This processing includes a
                        time filter and an energy filter.  The parameters
                        in this section are relevant to those two filters.

Figure 3  of the FELib PHA Parameters User Manual
                        is a useful description of these parameters and how they
                        drive signal processing.

****

**Name: **tfrisetime

**Data type: **64 element list of integers 4-250

**Default: **[lrepeate 80 64]

**Description: **
                                The rise time parameter for the time
                                fiter for each channel
                                expressed in digitizer samples.

**Name: **tfretriggerguard

**Data type: **64 element list of integers 0-1000

**Default: **[lrepeat 0 64]

**Description: **
                                The time filter retrigger guard for each
                                channel expressed in samples.

**Name: **efrisetime

**Data type: **64 element list of integers 4-1625

**Default: **[lrepeat 80 64]

**Description: **
                                The rise time parameter of the enegy filter
                                for each channel expressed in samples.

**Name: **efflattoptime

**Data type: **64 element list of integers 4-375

**Default: **[lrepeat 80 64]

**Description: **
                                The energy filter flattop time parameter
                                in units of samples for each channel.

**Name: **efpeakingpos

**Data type: **64 element list of integers 10-90

**Default: **[lrepeat 50 64]

**Description: **
                                The trapezoid peaking position for each channel
                                in percentage of the flattop time.  Note the
                                manual, at the time I'm writing this erroneously
                                expresses the limis on this parameter
                                at 0-100.

**Name: **efpeakingavg

**Data type: **list of 64 enumerated values

**Default: **[lrepeat 1 64]

**Description: **
                                Number of samples averaged to evaluate the
                                peak for each channel.  Legal values are
                                                                    1, 4, 16, 64

**Name: **efpolezero

**Data type: **list of 64 integers 4-65500

**Default: **[lrepeat 80 64]

**Description: **
                                Pole zero adjustment of the digital shaping
                                amplifier for each channel in units of samples.

**Name: **effinegain

**Data type: **list of 64 floating point values 1.0-10.0

**Default: **[lrepeat 1.0 64]

**Description: **
                                Sets the digital fine gain for each channel.
                                The granularity of these values is
                                0.001.

**Name: **eflflimitation

**Data type: **64 element list of bools

**Default: **[lrepeat false 64]

**Description: **
                                When enabled for a channel, a low frequency
                                filter is applied to that channel for the
                                energy filter.

**Name: **efbaselineavg

**Data type: **64 element list of enumerated values

**Default: **[lrepeat 16 64]

**Description: **
                                The number of samples averaged to compute the
                                signal baseline prior to the start of the
                                trapezoidal filter.  Legal values for each
                                element are:
                                0, 16, 64, 256, 1024, 4096, 16384.
                                Note that a value of 0
                                fixes the baseline at zero.

**Name: **efbaselineguardt

**Data type: **list of 64 integer values. 0-8000

**Default: **[lrepeat 0 64]

**Description: **
                                The time, for each channel, after the trapezoidal
                                filter before basline computation will resume.
                                These values are in units of nanoseconds.

**Name: **efpileupguardt

**Data type: **List of 64 integers 0-8000

**Default: **[lrepeat 0 64

**Description: **
                                For each channel, specifies, in ns, the guard time
                                that defines energy filter pileup.

## <a name="sec.eventstruct"></a>72.2.3.

This section describes events written by the Readout program.
                These hits are encapsulated in NSCLDAQ ringitems.  When the event
                builder is  in use, additional event builder encapsulation
                will occur.

Ring items are described in the NSCLDAQ documentation.
                This is in the form of an annotated header for
                DataFormat.h.  See e.g.
                [https://docs.nscl.msu.edu/daq/newsite/nscldaq-11.3/r22906.html](https://docs.nscl.msu.edu/daq/newsite/nscldaq-11.3/r22906.html).
                In order to support event building, the ring items that encapslate
                hits include a body header.  The body header includes the hit timestamp
                and sourceid as well as a zero valued barrier type.

The additional event builder encapsulation is described in the
                NSCLDAQ section on the event builder e.g.
                [https://docs.nscl.msu.edu/daq/newsite/nscldaq-11.3/x4509.html](https://docs.nscl.msu.edu/daq/newsite/nscldaq-11.3/x4509.html)

This leaves to us documenting the format of the body of a hit:

<a name="AEN16555"></a>**Table 72-1. Format of event body**

| Data Type | Contents |
| --- | --- |
| uint32_t | Number of uint16_t's in the event |
| Variable. | Null terminated string that identifies the module |
| uint16_t | Channel within the module the hit came from |
| uint64_t | Hit timestamp in nanoseconds |
| uint64_t | raw timestamp only meaningful if selected |
| uint16_t | fine timestamp only meaningful if selected |
| uint16_t | Peak height (energy) |
| uint16_t | Low priority flags. Only meaningful if selected. |
| uint16_t> | High priority flags. Only meaningful if selected. |
| uint16_t | Down sample selection code. Only meaningful if selected |
| uint16_t | Fail flags.  Only meaningful if selected |
| uint16_t | Analog probe type 1 - only meaningful if
                            analog probe 1 is selected for readout |
| uint32_t | Number of samples of analog probe 1 data.
                            This is zero if analog probe 1 is not selecte. |
| variable number of uint32_t values | Analog probe 1 values. |
| uint16_t | Analog probe type 2 - only meaningful if
                            analog probe 2 is selected for readout |
| uint32_t | Number of samples of analog probe 1 data.
                            This is zero if analog probe 2 is not selected. |
| variable number of uint32_t values | Analog probe 1 values. |
| uint16_t | Digital probe type 1 - only meaningful if digital probe 1 is selected |
| uint32_t | Number of samples in digital probe 1 |
| variable number of uint8_ts | Digital probe sample. |
| uint16_t | Digital probe type 2 - only meaningful if digital probe 2 is selected |
| uint32_t | Number of samples in digital probe 2 |
| variable number of uint8_ts | Digital probe sample. |
| uint16_t | Digital probe type 3 - only meaningful if digital probe 3 is selected |
| uint32_t | Number of samples in digital probe 3 |
| variable number of uint8_ts | Digital probe sample. |
| uint16_t | Digital probe type 4 - only meaningful if digital probe 4 is selected |
| uint32_t | Number of samples in digital probe 4 |
| variable number of uint8_ts | Digital probe sample. |

Note that if needed an additional byte will pad out the end of the
                event to bring it to an even number of uint16_t.
                However, since there are an even number of digital probes,
                all with the same length, I don't think this padding ever happens.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Support for CAEN Nextgen DPP-PHA digitizers | Up | Configuring SpecTcl |
