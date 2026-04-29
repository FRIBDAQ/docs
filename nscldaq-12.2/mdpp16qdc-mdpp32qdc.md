|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN103158"></a>mdpp16qdc, mdpp32qdc

<a name="AEN103162"></a>## Name

mdpp16qdc, meqq32qdc -- Suport the Mesytec MDPP16 and MDPP32 with QDC firmware

<a name="AEN103165"></a>## Synopsis

```
mdpp16qdc create name ?option value...?
mdpp16qdc config  name option value?..?
mdpp16qdc cget  name ?option?        

mdpp32qdc create name ?option value...?
mdpp32qdc config  name option value?..?
mdpp32qdc cget  name ?option?        
        
```

<a name="AEN103173"></a>## DESCRIPTION

This configuration command provides support for the Mesytec MDPP16, 16 channel
            and MDPP32 32 channel
             digitizers
            with charge digizing firmware (QDC firmware).  The configuration of this module is 
            relatively involved so you may want to refer to the
            [QDC firmware manual](https://www.mesytec.com/products/datasheets/MDPP-16_QDC.pdf)
            When looking at the configuration parameter documntation.  Look at
            [The MQDC32 QDC firmware manual](https://www.mesytec.com/products/datasheets/MDPP-32_QDC.pdf) for the 32 channel module.

<a name="AEN103178"></a>## OPTIONS



`-base` *vme-address*Configures the base address of the module.

`-id` *module-id*Identifying value the module will put into the data stream to identify the module
                            it came from.  This must
                            be in the rang 0-255 (8 bits) and should be unique across modules. If not configured,
                            this defaults to 0.

`-ipl` *IRQ-priority*The interrupt priority level at which the module will interrupt.
                            If this is zero, as it is if not configured, interrupts are disabled for the
                            module.

`-vector` *IRQ-status-id*If the module interrupts are enabled/used, this is the status id the module
                            wilil assert when it interrupts.

`-irqdatathreshold` *words*IF interrupts are used for this module, the module will interrupt when it has at
                            least this this number of 32 bit words buffered in its FIFO.  If not configured, 
                            this defaults to 1 which means the interrupt will happen as the first event is 
                            buffered.

`-maxtransfer` *words*Specifies the maximum number of words that can be read from the FIFO.
                            If the FIFO has more words availalble the module will terminate the transfer.

`-irqsourcde` *event | data*Determines when an interrupt happens if enalbed.  If event, the default if not configured,
                            the module interrupts when the event threshold is met (`-irqeventthreshold`), 
                            if data, when the `-irqdatathreshold` is met.

`-irqeventthreshold` *events*Sets the event threshold to use when interrupts are enabled and the 
                            `-irqsourceK` is set to event.  If not configured, the default is 3.

`-datalenformat` *8bit | 16bit | 32bit | 64bit | numevents*If not configured, this defaults to 32bit.  The only effect configuring this has on 
                            acquisition is that if 64bit is selected, the data read will be padded out to 
                            the next 64 bit boundary if needed with a "FIll dummy word" as described in 
                            the [QDC Firmware manual](https://www.mesytec.com/products/datasheets/MDPP-16_QDC.pdf)

`-multievent` *register-value*IF not set, this defaults to 0x0b.  See 
                            [The MDPP-16 manual](https://www.mesytec.com/products/datasheets/MDPP-16_SCP-RCP.pdf).  This value specifies the value for the register
                            at base + 0x6036 - the multi-event mode register.

`-marktype` *eventcount | timestamp | extended-timestamp*Determines what the module will put in the end of event trailer word.   By default, if not configured,
                            timestamp is selected.  If extended-timestamp is selected,
                            the module will add an additional 16 high order bits of timestamp.  See the FIFO format in the
                            [QDC Firmware manual](https://www.mesytec.com/products/datasheets/MDPP-16_QDC.pdf) for more details.

`-tdcresolution` *24ps | 49ps | 98ps | 195ps | 391ps | 781ps>*Selects the time resolution for the computed tdc. If not configured, defaults to 24ps.

`-outputformat` *register-value*The value to store in register at 0x6044, the output format register.  Only the bottom two bits
                            can  be selected, and the default value is 3 which is the power up value of that register.

`-adcresolution` *64k | 32k | 16k |  8k | 4k*The ADC resolution selected (register 0x6046).  If not configured this defaults to 
                            64k

`-windowstart` *offset-0-0x7fff*Start of the window of interest relative to the trigger. See register 0x6050 in 
                            the [The MDPP-16 manual](https://www.mesytec.com/products/datasheets/MDPP-16_SCP-RCP.pdf).   If not configured, this defaults to 0x3fbe.
                            This is in steps of 1.56ns.  The default value is about 81ns before the trigger.

`-windowwidth` *width-0-0x3ffff*Width of the window of interest.  If not configured, the default is 0x80 which
                            represents a window width of about 200ns.

`-firsthit` *true | false*If true, then only the first hit found in the region of interest is transmitted
                            in the event.  If not configured, this is true by default.

`-testpulser` *enabled | disabled*Turns on or off the test pulser.  This is off if not explicitly configured
                            to be enabled

`-pulseramplitude` *amplitude0-0xffff*If the `-testpulser` is enabled, this will be the amplitude of 
                            the test pulser pulses.  See register 0x6072 of  the
                            [The MDPP-16 manual](https://www.mesytec.com/products/datasheets/MDPP-16_SCP-RCP.pdf).

`-triggersource` *register-value*Defines the trigger.  The region of interest in the input signal is then defined
                            by `-windowstart` and `-windowwidth` relative to
                            when this trigger happens.  See register 0x6058 in the 
                            [The MDPP-16 manual](https://www.mesytec.com/products/datasheets/MDPP-16_SCP-RCP.pdf).  Only the bottom 10 bits of the value are used.
                            By default, 0 is written into this register if not configured.

`-triggeroutput` *register-value*Defines the signal that will be presented on the trigger output NIM out.
                            See register 0x605a.  See 
                             [The MDPP-16 manual](https://www.mesytec.com/products/datasheets/MDPP-16_SCP-RCP.pdf) for more information.  Note that 
                            only the bottom 10 bits of the value are used.  If not configured,
                            0 is written to this register

`-monitoron` *on | off *Enables or disables the monitor output.  See, however,
                            `-monitorch` and `-setwave` configuration options
                            to select what the monitor output show.  If not configured, this configures to
                            off by default.

`-monitorch` *channel-no*Selects the channel to use for the monitor outputs. The actual waveform
                            monitored in mon0 and mon1 will depend on the value of 
                            `-setwave`.  To see anything at those outputs, also
                            requires configuring `-monitoron` to on

`-setwave` *selection0-3*Determines which waveform in the FPGA processing of the waveform is
                            presented for the channel selected by `-monitorch` on the
                            Mon1 and Mon2 outputs.  See the discussion of the monitor outputs in the
                            description of the monitor outputs
                            [The MDPP-16 manual](https://www.mesytec.com/products/datasheets/MDPP-16_SCP-RCP.pdf)
                            for information about what the actual values of this option will select.  If
                            not configured, 0 is programmed, selecting the preamplifier output and trigger.

`-signalwidth` *register-values-8-element-list*This parameter value is an 8 element Tcl list of Signal widths.
                            The first element applies to channel 0 and 1, the second to 2 and 3 and so on.
                            For the MDPP32, each element of the  list is the width for a 
                            quad (set of four) channels.
                            See register 0x6110 in [QDC Firmware manual](https://www.mesytec.com/products/datasheets/MDPP-16_QDC.pdf) for more details.

`-inputamplitude` *register-values-8-element-list*List of the input amplitude values for channel pairs or quads. See register
                            0x6112 in [QDC Firmware manual](https://www.mesytec.com/products/datasheets/MDPP-16_QDC.pdf) for more details.

`-jumperange` *register-values-8-element-list*List of jumper range values for channel pairs or quads.  See 0x6114 in 
                            [QDC Firmware manual](https://www.mesytec.com/products/datasheets/MDPP-16_QDC.pdf) for more details.

`-qdcjumper` *8-element-list-of-bools*Elements should be true if the qdc jumper is in for the corresponding channel pair
                            or quad.
                            If not configured, this is 8 false values.

`-intlong` *register-values-8-element-list*List of long integrations times for channel pairs or quads.   In steps of 12.5ns. maximum
                            value is 506, minimum value 2.  If not programmed, this defaults to 8 elements of 16.

`-intshort` *register-values-8-element-list*List of short integration values for channel pairs or quads.  In steps of 12.5ns, 
                            minimum value is 1, maximum value 127.  If not explicitly programmed,
                            this defaults to 8 elements of 2.

`-threshold` *register-values-16-element-list*List of channel trigger threshold values, one per channel.  Values can be
                            in the range 0 to 0xffff.  IF not explicitly programmed, this defaults to a list
                            of 16 0x4ff values.  Note that there are 16 elements in the list, there is a threshold
                            for each channel, not a common one for the pair.
                            Note that for the MQDC32 this is a 32 element list not a 16 element list so, again,
                            there is a threshold specification for every channel.

`-resettime` *register-values-8-element-list*The reset time for each channel pair/quad for the preamp.  If not programmed, this defaults
                            to 8 elements of 32 which is normally sufficient.  Values can range from 0-0x3ff
                            and the time is in 12.5ns steps.

`-gaincorrectionlong` *8-element-list-with: div4 | mult4 | none*Gain corrections for the long integration time(?).   If not programmed, defaults to 8 elements of
                            none

`-gaincorrectionshort` *8-element-list-with: div4 | mult4 | none*Gain corrections for short integration interval.  See `-gaincorrectionlong`

`-trigtoirq` *list-of-7-channel-masks*When the module is used in interrupt mode, each element of this list directs the
                            interrupt priority level of the interrupt for that set of channels.
                            Each channel should only appear at most once.  The first element of the list is
                            the mask of channels that will fire IRQ1, the second IRQ2 and so on.

For the MQDC 32, this is a 14 element list.  The first element of the list
                            are the channel mask for IRQ1 channels 0-15 and the second list element
                            the channel mask for IRQ1 for channels 16-31 and so on.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| marker | Up | mdpp32scp |
