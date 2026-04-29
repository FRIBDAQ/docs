|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN7152"></a>Chapter 13. Simple V775 readout

# <a name="AEN7154"></a>13.1. Introduction

This document will show how to take data from NSCLDAQ, and analyze it
            with SpecTcl using a CAEN
            V775 32 channel TDC.
            We are going to:



- Show a simple electronics setup that will send test pulses into
                  the V775.
- Show how to use the SBS readout framework to read events
                  from the V775
- Show how to use NSCLSpecTcl to create raw spectra for the TDC
                  online.

This paper assumes that you are at least somewhat familiar with Linux
            since the DAQ software runs on a Linux box. It also assumes that you a
            little familiar with C++. Finally it will be helpful if you know how to use
            an oscilloscope, as that will be needed to setup your electronics.
            All the code is available at:
            [http://docs.nscl.msu.edu/daq/samples/caenv775/code.zip](http://docs.nscl.msu.edu/daq/samples/caenv775/code.zip)

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Conclusion | Up | Setting up the Electronics. |
