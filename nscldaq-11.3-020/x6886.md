|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 15. XLM72 Gate Delay Control GUI | Next |


---

# <a name="AEN6886"></a>15.2. Setting up an XLM72 as a gate delay generator for remote control

The support for the gate delay generator is provided within VMUSBReadout.
      Among other support for this device, NSCLDAQ provides a high level driver
      that can satisfy requests to the device from remote clients of the slow
      controls server.  The first thing that the user will need to do to set up
      the device is to load a proper gd16.bit firmware on the device. To do so,
      the user should make use of the "xlm" slow controls module. This module
      specifically loads firmware onto the specified device and can be used to
      verify a firmware signature. Let's assume that we have an XLM72 device in
      slot 10 and want to turn it into an gate delay generator. I will also
      assume that this is being run on the NSCL network and has access to
      /user/s800/server/fpga/gd16.bit. Given those assumptions, the following
      lines should be added to the ctlconfig.tcl file:

```
set slot 10
Module create xlm xlmloader
Module config xlmloader -base [expr {$slot << 27}]
Module config xlmloader -firmware [file join /user s800 server fpga gd16.bit]
Module config xlmloader -validate on -signature [expr 0xdaba0006]
    
```

All this does is create a slow controls module called "xlmloader" and
      then pass a series of configuration options to. The first configuration
      option is -base, which specifies the base address of the XLM72 device we
      wish to talk to. The XLM72 I am using is geographically addressed and
      thus responds to the address formed by bit shifting the slot number up 27
      bits. The next option we set is the location of the firmware (i.e.
      /user/s800/server/fpga/gd16.bit). We then also tell the xlmloader module
      that we want it to check that the firmware is loaded properly by setting
      the -validate option to "on". The idea here is that the gd16.bit firmware
      will set a register in the fpga to 0xdaba0006 when properly loaded. Note
      that the signature is specific to this firmware and could be different if
      using a different version of the gd16.bit firmware. If in doubt, contact
      Daniel Bazin for the proper firmware signature to use.

|  |  |
| --- | --- |
|  | If you are using different
        firmware than gd16.bit, you should have no expectation that any NSCLDAQ
        drivers will work properly. Remember that the gate and delay generator's
        behavior is defined by both the hardware and the firmware. If you choose
        to use a different firmware, you are essentially using a different module
        than any of the drivers in NSCLDAQ were written to support. |


With the above lines added to the ctlconfig.tcl file, the module will be
      configured when VMUSBReadout starts up and whenever the user calls the
      "init" command at the console. At this point, we have a gate delay
      generator but have no way of communicating with it remotely via the
      XLM72GateDelayControl GUI. To do that we need to add a few more lines to
      the ctlconfig.tcl after the ones you have already added. Those lines are:

```
lappend auto_path [file join $::env(DAQROOT) TclLibs]
lappend auto_path $::env(DAQLIB)

package require snit
package require gd16xlm72

AGD16XLM72Control gd16controlObj -slot $slot
Module create tcl GD16control
Module config GD16control -ensemble gd16controlObj
    
```

The first three lines here are very important because it specifies that
      we want to use the gd16xlm72 package in the tclsh and also where to look
      find it. The gd16xlm72 contains the actual drivers for communicating with
      the XLM72 once it has the proper firmware loaded on it. The driver that
      handles remote requests through the slow controls server is called
      AGD16XLM72Control. This is what is called a snit::type in the language of
      tcl, but that is not terribly important. You can feel free to treat this
      as a magic box. The only specific aspect to the line beginning with
      "AGD16XLM72Control" that is important for you to set to your specific
      situation is the value passes to the -slot option. In our example this
      should be 10, which it is based on the code we already added to the
      ctlconfig.tcl file. The final two lines are how we load a snit::type
      driver into the slow controls server as with the module name of
      "GD16control".  The module name is very important to remember because it
      must be passed to the XLM72GateDelayControl application when launched.

With that, you should now have a proper ctlconfig.tcl to use an XLM72 as
      a gate delay generator if it is in slot 10.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| XLM72 Gate Delay Control GUI | Up | Launching the XLM72GateDelayControl |
