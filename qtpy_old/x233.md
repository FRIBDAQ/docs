|  |  |  |
| --- | --- | --- |
| SpecTcl DDAS Unpackers Guide. |
| Prev | Chapter 4.CFileDrivenParameterMapper | Next |


---

# <a name="AEN233"></a>4.2. `CCalibratedFileDrivenParameterMapper`

This class produces two parameters for each hit.  The first is the
            same raw parameter `CFileDrivenParameterMapper`
            unpacks.  The second is a calibrated energy parameter.

The calibrated enery is computed by passing the raw energy through
            a quadratic function.  The configuration file provides the
            coefficients of this function as either constants, or tree
            variable names (or a mix).  The configuration file
            also provides a more general definition of the calibrated
            treeparameter (low, high bins, and units).

Construction of the
            `CCalibratedFileDrivenParameterMapper`
            is identical to that of `CFileDrivenParameterMapper`.
            We will therefore refer you to the usage examples for that
            class rather than repeating all that stuff here.

The difference in usage of these to classes is the configuration
            file.  Of necessity, the
            `CCalibratedFileDrivenParameterMapper`,
            while following similar formatting rules requires additional
            fields of information.

Following the name of the raw parameter are the three
            coefficients for the quadratic function used to produce the
            calibrated parameter.  In order these are the constant, linear and
            quadratic coeficients.  Each field can be either a constant
            floating point or the name of a tree variable (which will
            be created if necessary).

Thus linear calibration is simply a matter of providing
            a constant quadratic coefficient of 0.0

Following the coefficients are four fields that describe the resulting
            treeparameter.  The first three are numeric and are the low and
            high limits of the parameter and the binning.  The last is textual
            and provides the units for the parameter.  Note that the text
            "" can be used if no units are required.

The final field is the name of the calibrated parameter.
            As with the raw parameter, a tree parameter is created if necessary.

Here's an example of configuration file lines:

<a name="AEN251"></a>```
0 2 0 crate0.slot2.raw.chan0 c0.s2.ch0.const c0.s2.ch0.lin 0 0 100 100 MeV crate0.slot2
            
```

Note how the quadratic coefficient is constant 0?  This results in
            a linear calibration function.

<a name="AEN254"></a>```
0 2 0 crate0.slot2.raw.chan0 c0.s2.ch0.const c0.s2.ch0.lin c0.s2.ch0.q 0 100 100 MeV crate0.slot2.cal.chan0                
            
```

The line above is a fully quadratic calibration.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CFileDrivenParameterMapper | Up | Reference pages. |
