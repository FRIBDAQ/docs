|  |  |  |
| --- | --- | --- |
| VMUSBSpecTcl |
| Prev |  | Next |


---

# <a name="AEN30"></a>Chapter 2. VMUSBSpecTcl  configuration

VMUSBReadout uses a Tcl configuration file to define and configure
            devices in the VME crate and to select the order in which they
            are read out for each stack.

Normally one has a primary event stack and a scaler stack however,
            the hardware, and software, support a total of 8 stacks with
            differing trigger conditions including front panel, timed and
            VME interrupts.

By adding a small amount of metadata to the configuration file,
            the same information can be used by SpecTcl to select the order in
            which it runs unpacking objects that understand the format of data
            from each module, and distribute data from each channel into
            parameters.  Furthermore, once those raw parameters are known, the
            SpecTcl configuration processing creates raw spectra for each
            parameter that has been defined.

The primary bit of metadata required by VMUSBSpecTcl is  Tcl array
            named `adcChannels`.  This array is indexed by
            module name  and each element contains a list of the parameter names
            to be associated with the input channels of the digitizer.
            If a channel is unused, use an empty string ("").
            If the last several channels are unused you can just supply a shorter
            list.

The remainder of this chapter are a set of examples that
            show how you can define the parameters of a CAEN V785 peak
            sensing ADC module you have named adc.
            The first example shows how to use a Tcl loop to define
            parameters named adc.00 through
            adc.31.  The Tcl
            **format** command is used to ensure that
            the channel number has leading zeroes if needed.
            **lappend** (list append)
            is used to construct the list an element
            at a time each pass through the loop.

<a name="AEN44"></a>**Example 2-1. Using a loop to create parameters**

```
for {set i 0} {$i < 32} {incr i} {
    lappend adcChannels(adc) [format adc.%02d $i]
}
            
```

The next example equivalent to the previous one but much more
            work to write.  Something like this may be needed, however if your
            parameter names don't occur in sets with some regular pattern
            (remember that you could have several for or foreach loops all
            lappending to the same `adcChannels` element).

<a name="AEN49"></a>**Example 2-2. Creating parameter names the long way**

```
set adcChannels(adc) [list adc.00 adc.01 adc.02 adc.03 adc.04 \
                             adc.05 adc.06 adc.07 adc.08 adc.09 \
                             adc.10 adc.11 adc.12 adc.13 adc.14 \
                             adc.15 adc.16 adc.17 adc.18 adc.19 \
                             adc.20 adc.21 adc.22 adc.23 adc.24 \
                             adc.25 adc.26 adc.27 adc.28 adc.29 \
                             adc.30 adc.31                      \
                        ]
            
```

The next example shows how to declare define the same ADC, if you
            are not using channels 5 through 9.

<a name="AEN53"></a>**Example 2-3. Unused parameters in the middle**

```
set adcChannels(adc) [list adc.00 adc.01 adc.02 adc.03 adc.04 \
                             ""     ""     ""     ""     ""     \
                             adc.10 adc.11 adc.12 adc.13 adc.14 \
                             adc.15 adc.16 adc.17 adc.18 adc.19 \
                             adc.20 adc.21 adc.22 adc.23 adc.24 \
                             adc.25 adc.26 adc.27 adc.28 adc.29 \
                             adc.30 adc.31                      \
                        ]
            
```

Finally, if you are only using the first 8 channels of the
            ADC (channels 0-7):

<a name="AEN57"></a>**Example 2-4. Onl using the first few channels**

```
for {set i 0} {$i < 8} {incr i} {
    lappend adcChannels(adc) [format adc.%02d $i]
}
            
```

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Introduction and background |  | Extending VMUSBSpecTcl |
