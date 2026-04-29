|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 4. VMUSBReadout | Next |


---

# <a name="AEN802"></a>4.3. Writing the Configuration Script

Configuring the VM-USB for readout requires no compilation of code or
      writing of C++, rather it amounts to writing a simple configuration
      script, daqconfig.tcl, that is written in the TCL language. In general,
      one does not need to know how to write TCL to create their config file.
      Instead, knowing the names of the device driver commands and their
      arguments should be enough.          
      [[1]](#FTN.AEN805)
      On the other hand, if you are TCL savvy, then go ahead and
      write standard TCL in the script, because it is evaluated with the
      standard TCL interpeter.

As was mentioned in the previous section, the VM-USB requires the
      definition of a "stack", i.e., a list of VME operations that should be executed
      given a specific trigger condition, and the configuration script is where
      this is done. You can imagine that every device in an experiment
      is read out using a well-defined set of VME operations so that if
      more than one device needs to be read out, the stack can be constructed by
      appending each successive device's readout operations to it. This is
      exactly what is done. In fact, VMUSBReadout provides support for readout
      of many commonly used devices out of the box. The user simply needs to
      declare which of devices he/she is using and then add them to a stack.

Each supported device class is represented in the configuration file by
      a Tcl command ensemble. The command ensemble provides subcommands that
      allow you to create, configure, and query the configuration of physical
      devices (device instances). The device configuration is represented in
      the configuration file in a manner analagous to the state of a Tk widget.
      That is, you never actually program the device directly, you simply
      specify the desired configuration. The actual programming is done by the
      device class's device support software. Device instances are created with
      a user-provided name that must be unique, because specific device
      instances are always identified by their name later in the script.

In accordance with the way the VM-USB operates, you can define up to 8
      stacks in the configuration script. Just like the device classes, stacks
      are represented as command ensembles that can create, configure, and query stack
      instances. The user adds their specific device instances to a stack
      by passing them as list to the `-modules`
      configuration option. Furthermore, the trigger condition for the stack
      is specified by the `-trigger`. It is important to
      understand that unless a device instance is registered to a stack
      instance, the VM-USB will ignore its presence.

The DAQ configuration file is processed at the beginning of each run and
      in a fresh interpreter each time. What this means practically is that
      state cannot be maintained across runs via your configuration file.

<a name="AEN815"></a>**Example 4-1. Creating and configuring devices**

Some things are best demonstrated than explained in prose. For that
        reason, we will conclude our discussion of the configuration file by
        walking through the set up of a basic daqconfig.tcl file. This script
        will focus on configuring a system to read out a single Caen V785
        peak-sensing ADC in slot 15, with base address 0x11000000. We will also
        readout out a Struck SIS3820 scaler every two seconds.

The name of the command ensemble that does this is
        **adc**, so we add the following two lines to our
        daqconfig.tcl file.

```
adc create myadc 0x11000000     
adc config myadc -geo 15        
      
```

The **adc** command implements base support for the
        CAEN 32 channel digitizer family (V775, V785, V792, V862).

[[x802#vmusb.config.create]]            This line creates an instance of one of those modules with a base address
            0x11000000.  The instance is given the name
            myadc to uniquely identify it later in the script.
          [[x802#vmusb.config.config]]            The second line sets a configuration parameter, the geographical
            address of the  module, for the instance created by the first line.
            The reference ssection 3vmusb provides detailed
            information about the configuration options supported by each
            device class.

Configuration files must also specify at least one stack and, if
        scaler modules are to be read periodically, a second scaler stack.
        See the [[r64692]] command
        in the reference material for detailed information about how
        to create and configure stacks.

To continue building on the daqconfig.tcl that was just created, we
        will add a stack that will read out myadc.

```
stack create events 
stack config event -trigger nim1 -modules [list myadc]
      
```

Stacks are created and configured exactly like any other module.  In
        this configuration file fragment, a stack named
        events is created.  It is configured to manage the
        myadc module (`-modules`).  as well as
        to be executed when a NIM signal arrives at the IN 1 input of the VM-USB
        (-trigger nim1).

Finally, we add the SIS3820 scaler to the configuration script and
        create a second stack specifically for reading the scalers. Because this
        is logically equivalent to what we did to set up the Caen V785, we will
        be a bit more terse. Here are the lines that need to be added to the
        daqconfig.tcl for reading out the scaler every 2 seconds.

```
sis3820 create sisscaler 0x38000000       

stack create scaler 
stack config scaler -modules [list sisscaler] -trigger scaler -period 2  
      
```

[[x802#vmusb.config.sis3820]]            Here we create the device instance for the SIS3820. We are using the 
            device to read all 32-channels during each read operation which is
            accomplished without anything other than default settings.
          [[x802#vmusb.config.sclrStack]]            Because we want to execute the stack every 2 seconds, we must
            provide the scaler value to the
            `-trigger` option. Furthermore, we must also provide
            the number of seconds for the period of execution to the
            `-period` option.

The reference pages in 3vmusb describe, among other
      things the commands that implement device support that are supported by
      the NSCL programming group.  In addtion to user device drivers that are
      described later in this chapter, two device drivers support modules have
      been contributed by Washington University at St. Louis.  These modules
      support XLMs used to read out the ASIC systems they have developed for
      managing large detector arrays.

For information about how to use those modules, contact Lee Sobotka or Jon
      Elson at Washington University directly.

If the device support provided by VMUSBReadout
      is insufficient for your experiment, you can extend the supported modules
      by developing your own module. The details of extending device support can
      be found in [[x1146]].

### Notes

|  |  |
| --- | --- |
| [1] | Because TCL is a full blown programming language, it has rules for
          syntax.  If you know zero TCL, it may happen that you unknowingly
          violate one of the syntax rules when writing your daqconfig.tcl
          script. You will know you did if you begin a run and VMUSBReadout
          fails to transition to data taking because of a TCL error. In that
          case, you might have to learn a little bit of the TCL syntax to fix
          it. Do not fret though, TCL isverysimple and
          nowhere near as complicated as other languages like C++. Here is a
          reasonable starting pointhttp://www.tutorialspoint.com/tcl-tk/index.htm. |

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Basic Tenets of VM-USB Operation | Up | The Slow-Controls Subsystem |
