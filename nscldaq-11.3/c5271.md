|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN5271"></a>Chapter 10. A Simple VMUSBReadout Experiment Tutorial

# <a name="AEN5273"></a>10.1. Introduction

NSCLDAQ distributes with it a program called VMUSBReadout that supports
      the readout of the Wiener VM-USB VME controller. The following document
      will instruct the reader in how to set up a basic experiment consisting of
      a CAEN V785 peak sensing analog-to-digital converter, a CAEN V775
      time-to-digital converter, and a Struck SIS3820 32-channel latching
      scaler. The level at which this tutorial is written assumes the following:



- No programming experience in Tcl
- Some familiarity with the C++ language
- Access to the required electronics
- Ability to wire up a signal processing circuit from a block diagram
- A version of NSCLDAQ 11 has been installed on the system in
            /usr/opt/nscldaq/11.x-yyy, where x is any minor
            version and yyy is any path version.
- The reader has already read the
            VMUSBReadout User's Guide found at the
            NSCLDAQ [website](http://docs.nscl.msu.edu/daq) or
            in the /usr/opt/nscldaq/11.0/share/pdfs
            directory.

In addition to simply setting up the experiment, the user will be
      instructed at how to interpret the output of the devices using the dumper
      program for simple debugging and then on how to develop a basic SpecTcl
      application tailored to the specific experiment. The SpecTcl
      implementation will give an example of how to write an event processor
      using a framework independent data unpacker as well as supporting its
      potential reuse on event built data.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| simple-setups | Up | Setting up the Electronics |
