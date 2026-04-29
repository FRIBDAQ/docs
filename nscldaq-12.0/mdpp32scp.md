|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="vmusb3-mdpp32scp"></a>mdpp32scp

<a name="AEN84310"></a>## Name

mdpp32scp -- Mesytec MDPP-32 module with SCP firmware

<a name="AEN84313"></a>## Synopsis

**mdpp32scp create *name -base base [option1 value1 option2 value2 ...]*
**

**mdpp32scp config *name option value ...*
**

**mdpp32scp cget *name*
**

<a name="AEN84323"></a>## DESCRIPTION

This command creates, configures and retrieves the configuration of
                 Mesytec MDPP-32 module with SCP firmware.

Use the **create** subcommand to create a new module instance
                 providing it with a unique `name` that will
                 be used to identify it in future commands.  The `-base`
                 parameter is the base address of the module as set in the module rotary
                 switches. Options and corresponding values can be provided with the
                 **create** subcommand instead of using **config**
                 subcommand to configure.

Use the **config** subcommand to configure
                 a module named `name`  the `option`
                 options and legal values are described in the section OPTIONS below.

The **cget** subcommand returns as its value the configuration
                 of the module `name`.  The configuration is
                 returned as a list of two element sublists where each sublist
                 contains, in order, an option from OPTIONS below, and its value.
                 Note that some values may themselves be lists.

<a name="AEN84339"></a>## OPTIONS



`-base` *value*Allows you to reconfigure the base address of a module.
                             This defaults to 0. The required
                             `-base` parameter of the create
                             option for this device overrides the default value.

`-id` *vsn*`vsn` will be used as the module's
                             identifier or *virtual slot number*.
                             The `vsn` will be encoded into the
                             event data that is returned by the module. This, in turn
                             is normally used by event decoders to determine which parameters
                             the channels of the module should be unpacked into.

Each module should be given a unique `vsn`.

By default, the value is 0.

`-ipl` *0-7*The interrupt priority level the module should use to request
                             a VME bus interrupt. Normally interrupts will be used
                             to trigger an interrupt triggered stack.

By default, the value is 0.

`-vector` *0-255*The interrupt vector the module should use. The vector value is ignored if
                             the module interrupts are disabled.

Note that the VMUSB processes 16 bit vectors, but the
                             vector produced by this module is 8 bits wide.
                             The VME standard is ambiguous about how such modules
                             produce the top eight bits of the vector under these
                             circumstances.  These modules set those top bits
                             to zero.  E.g. `-vector ` 0x80
                             produces a vector, as see by the VMUSB of 0x0080

By default, the value is 0.

`-irqeventthreshold` *0-32767*(From MDPP-32 SCP documentation) Every time the number of events in the FIFO
                             exceeds this threshold, an IRQ is emitted.

The register length is 15 bit. Thus, the maximum number it can take should be
                             0x3FFF (32757)

By default, the value is 1.

`-irqdatathreshold` *0-32256*(From MDPP-32 SCP documentation) Every time the number of 32 bit words in
                             the FIFO exceeds this threshold, an IRQ is emitted. Maximum allowed threshold
                             is "FIFO size".

"FIFO size" in the SCP documentation is 32k-512=32256.

By default, the value is 1.

`-irqsource` *event|data*

eventUse the value provided with `-irqeventthreshold` as
                                         the IRQ threshold.

dataUse the value provided with `-irqdatathreshold` as
                                         the IRQ threshold.

By default, the value is data

`-maxtransfer` *0-32256*(From MDPP-32 SCP documentation) With
                             "`-multievent` 3", the value specifies
                             the amount of data read from FIFO before Berr is emitted. Transfer stops
                             only after full events.

e.g. With "`-maxtransfer` 1", 1 event
                             per transfer is emitted.

With "`-multievent` 0xb", the value specifies
                             the number of events read from FIFO before Berr is emitted.

Setting this option to 0 allows unlimited transfer.

By default, the value is 1.

`-datalenformat`
*8bit | 16bit | 32bit | 64bit | numevents*

numeventsShow number of events in FIFO

(From MDPP-32 SCP documnetation) The number of 32 bit words is always even.
                             If necessary the fill word "0" is added. For the setting 0
                             and 1, the max value 0xFFFF is shown
                             when number exceeds the 16 bit format. The FIFO is not affected.

By default, the value is 32bit.

`-multievent` *See detail*By default, the value is 0.

<a name="AEN84464"></a>```
+-----------------------------------------+
|     Bit[3]     |   Bit[2]   | Bit[1:0]  |
+-----------------------------------------+
|  count events  | skip Berr, | mode[1:0] |
|   not words    | send EOB   |           |
| (reg. 0x601A)  |            |           |
+-----------------------------------------+
                             
```



Bit[1:0](From MDPP-32 SCP documentation)

Allow multi event buffering.



0Not allowing multi event buffering

Register 0x6034 clears events
                                                     allowing new conversion.

1Allowing multi event buffering

Unlimited transfer. No readout reset required.
                                                     Register 0x6034 can be written
                                                    after block readout. Don't use for CBLT.

3Allowing multi event buffering, but MDPP transfers
                                                     limited amount of data.

The number of data words can be specified via
                                                     register 0x601A After word limit is
                                                     reached, the next end of event mark terminates transfer
                                                     by emitting Berr. So, register 0x601A=1
                                                     means event by event transfer (Berr after each event).

The next data block can be transferred after writing
                                                     the register 0x6034 (resets Berr).

Bit[2]Berr handling. If set, send EOB=bit[31:30]=bx10
                                         instead of Berr.

Bit[3]Compare number of transmitted events (not words!) with the register
                                         0x601A value (`-maxtransfer` value)
                                         for Berr condition.

`-marktype`
*eventcount | timestamp | extended-timestamp*By default, the value is eventcount.



eventcount, timestampThe last 32 bit word in the data contains either event counts
                                         or timestamp according to the setting.

<a name="AEN84526"></a>```
+------------------------------+
|  2  |           30           |
+------------------------------+
| b11 | eventcount / timestamp |
+------------------------------+
                                         
```

extended-timestampFollowing 32 bit word will be added to the data.

<a name="AEN84533"></a>```
+------------------------------------------------------+
|  2  |  2  |       12       |           16            |
+------------------------------------------------------+
| b00 | b10 | xxxx xxxx xxxx | 16 high bits time stamp |
+------------------------------------------------------+
                                         
```

`-tdcresolution`
*24ps | 49ps | 98ps | 195ps | 391ps | 781ps*Just for your information, TDC resolution is calculated using the
                             raw register value with formula: 25ns/pow(2, 10-value)

By default, the value is 781ps.

`-adcresolution`
*64k | 32k | 16k | 8k | 4k*Just for your information, ADC resolution is calculated using the
                             raw register value with formula: pow(2, 6-value)k

By default, the value is 4k.

`-outputformat` *0-3*

0Time and long integral

1Long integral only (SCP mode)

2Time only (TDC mode)

3Long integral, short integral and time

By default, the value is 3.

`-windowstart` *int 0-32767 (0-0x7fff)*(From MDPP-32 documentation) Unit: 1.56 ns (=25ns/16)

Start window of interest: 0x0000 start at -25.56us, 0x7FFF start at +25.56us, 0x4000 = 16k no delay.

< 16k, window starts before Trigger, > 16k, window is delayed.

By default, this parameter is 0x3fc0(=16320).

`-windowwidth` *int 0-16383 (0-0x3fff)*(From MDPP-32 documentation) Unit: 1.56 ns, max 16k = 25.56 us

By default, this parameter is 0x20(=32).

`-firsthit` *0 | 1*

0transmit all hits in the window

1 (default)only transmit first hit

`-testpulser` *0 | 1*Switch for the internal test pulser.

`-pulseramplitude` *int 0-4095 (0-0xfff)*(From MDPP-32 documentation) Max value corresponds to about 30% at gain=1.
                             Gain jumpers are situated before pulser coupling,
                             so have no effect on the pulser amplitude.

This value has no effect unless `-testpulser` is set 1.

`-triggersource` *int 0-1023 (0-0x3ff)*(From MDPP-32 documentation) Defines the trigger which creates the window of interest.
                             This can be: one or both of the trigger inputs, lower 16 channels(B0), upper 16 channels(B1),
                             or both banks (all channels).

<a name="AEN84632"></a>```
+-------------------------------------------+
| Whole bank |    16 channels     |  trig   |
|   2 bits   |       6 bits       | 2 bits  |
+-------------------------------------------+
|  B1  | B0  | active | Chan[4:0] | T1 | T0 |
+-------------------------------------------+
                             
```

The default value is 0x100.

`-triggersource` *int 0-1023 (0-0x3ff)*(From MDPP-32 documentation) Defines the trigger which creates output trigger.
                             This can be: one or both of the trigger inputs, lower 16 channels(B0), upper 16 channels(B1),
                             or both banks (all channels).

<a name="AEN84641"></a>```
+-----------------------------------------+
| Whole bank |    16 channels     |   00  |
+-----------------------------------------+
|  B1  | B0  | active | Chan[4:0] | 0 | 0 |
+-----------------------------------------+
                             
```

The default value is 0x100.

`-tfintdiff`
*int[8] 1-127*TF integration/differentiation time in 12.5 ns unit

The parameter provided must be a list of 8 integers.
                             The value of an element at index[0-7] is applied
                             to the channels [4*index, 4*index+3].

By default, the value is [list 20 20 20 20  20 20 20 20],
                             which is 250 ns for all channels.

`-pz`
*int[32] 64-65535*Signal decay time in 12.5 ns unit. Allowed range is [64-64000] and 65535.
                             Setting 65535 means infinite decay time.

The parameter provided must be a list of 32 integers. Each element sets
                             the decay time to each channel.

By default, the value is
                             [list 0xffff 0xffff ... 0xffff 0xffff],
                             which is infinite decay time for all channels.

`-gain`
*int[8] 100-25000*Gain. 100 means gain 1. 25000 means gain 250.

The parameter provided must be a list of 8 integers.
                             The value of an element at index[0-7] is applied
                             to the channels [4*index, 4*index+3].

By default, the value is [list 200 200 200 200  200 200 200 200],
                             which is gain 2 for all channels.

`-threshold`
*int[32] 0-64000*

The parameter provided must be a list of 32 integers. Each element sets
                             the threshold to each channel.

By default, the value is
                             [list 2000 2000 2000 2000 ... 2000 2000 2000 2000].

`-shapingtime`
*int[8] 0-65535 (mV)*Range printed on the jumper installed on the module in mV.

The parameter provided must be a list of 8 integers.
                             The value of an element at index[0-7] is applied
                             to the channels [4*index, 4*index+3].

By default, the value is
                             [list 3072 3072 3072 3072  3072 3072 3072 3072],
                             which is 3072 mV for all channels.

`-blr`
*int[8] 0 | 1 | 2*Base line restorer setting.

0: Off, 1: Strict (int. time = 4 shaping times), 2: Soft (int. time = 8 shaping times)

The parameter provided must be a list of 8 integers.
                             The value of an element at index[0-7] is applied
                             to the channels [4*index, 4*index+3].

By default, the value is [list 2 2 2 2  2 2 2 2],
                             which is soft for all channels.

`-signalrisetime`
*int[8] 0-127*Signal rise time in multiple of 12.5 ns.

(From MDPP-32 SCP documentation) It determines the flat top of trapezoidal shape.
                             0 -> For Si-detectors, constant rise time detectors: shorted dead time.
                             For germanium detectors with position dependent rise time set
                             to largest possible signal rise time.
                             This results in highest resolution and ballistic loss correction.

The parameter provided must be a list of 8 integers.
                             The value of an element at index[0-7] is applied
                             to the channels [4*index, 4*index+3].

By default, the value is [list 0 0 0 0  0 0 0 0],
                             which is 0 (0*12.5=0ns) for all channels.

`-printregisters` *0 | 1*Print out register values from the module. The values are not from the user input,
                             but from the actual register values read from the module after processing the input.

<a name="AEN84725"></a>## EXAMPLES

<a name="AEN84727"></a>**Example 1. Sample MDPP-32 SCP commands**

```
set tfintdiff         [list 100 16 16 16  16 16 16 16]
set pz                [list 0xFFFF 0xFFFF 0xFFFF 0xFFFF  0xFFFF 0xFFFF 0xFFFF 0xFFFF \
                            0xFFFF 0xFFFF 0xFFFF 0xFFFF  0xFFFF 0xFFFF 0xFFFF 0xFFFF \
                            0xFFFF 0xFFFF 0xFFFF 0xFFFF  0xFFFF 0xFFFF 0xFFFF 0xFFFF \
                            0xFFFF 0xFFFF 0xFFFF 0xFFFF  0xFFFF 0xFFFF 0xFFFF 0xFFFF]
set gain              [list 200 200 200 200  200 200 200 200]
set threshold         [list 2000 2000 2000 2000  2000 2000 2000 2000 \
                            2000 2000 2000 2000  2000 2000 2000 2000 \
                            2000 2000 2000 2000  2000 2000 2000 2000 \
                            2000 2000 2000 2000  2000 2000 2000 2000]
set shapingtime       [list 100 100 100 100  100 100 100 100]
set blr               [list 2 2 2 2  2 2 2 2]
set signalrisetime    [list 0 none none none  none none none none]
set windowStart         16368
set windowWidth         32
set firstHit            1
set testPulser          0
set pulserAmplitude     400
set triggerSource       0x100
set triggerOutput       0x100

mdpp32scp create scp -base 0x00030000
mdpp32scp config scp -tfintdiff $tfintdiff \
                     -pz $pz \
                     -gain $gain \
                     -threshold $threshold \
                     -shapingtime $shapingtime \
                     -blr $blr \
                     -signalrisetime $signalrisetime \
                     -windowstart $windowStart \
                     -windowwidth $windowWidth \
                     -firsthit $firstHit \
                     -testpulser $testPulser \
                     -pulseramplitude $pulserAmplitude \
                     -triggersource $triggerSource \
                     -triggeroutput $triggerOutput \
                     -printregisters 1
                 
```

Defines a module with base address 0x00030000.
                 While many register values are defined with lists, not all of them are
                 used to configure the module (qdcJumper
                 is not used).

If any of the parameters are not specified in config,
                 it uses the default values.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| mdpp32qdc | Up | CVMUSB |
