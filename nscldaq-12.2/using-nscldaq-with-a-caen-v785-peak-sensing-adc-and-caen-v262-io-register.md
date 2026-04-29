|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN9586"></a>Chapter 16. Using NSCLDAQ with a CAEN V785 Peak-Sensing ADC and CAEN V262 IO Register

# <a name="AEN9588"></a>16.1. PREFACE

This paper's purpose is to guide the reader through the process of
      setting up and reading data from a CAEN V785 peak-sensing ADC using an SBS
      Bit3 PCI/VME bridge. The trigger for the readout of the device in this
      tutorial will be initiated by a CAEN V262 IO Register and the data read
      out will be formatted in a "packet" structure. Furthermore, we will
      demonstrate how to do this in way that generates data with body headers.

This tutorial will encompass the steps to get the 
      system running from start to finish. In doing so, it will cover how to
      set up the electronics and how to modify the SBS Readout software
      skeleton. The targeted version of NSCLDAQ software will be 11.0.
      Testing for the code is also covered to a limited extent.

This paper assumes that you are



- Somewhat familiar with Linux.
- Familiar with the C++ programming language at a basic level.
- Familiar with an oscilloscope.

The final version of the software is available for download at:
      *MAKE THE LINK CORRECT!*

Every effort has been made to ensure the accuracy of this document.
      As authors we take very seriously reports of mistakes, omissions, and
      unclear documentation. If you come across a part of the document you
      think is wrong, needs expansion, or is not clearly worded, please
      report this to `<helpme@nscl.msu.edu>`. We will correct this problem
      as soon as possible and, if you like, credit you publicly in the
      document for finding and helping us fix this issue.

It will be assumed that the user has a valid NSCLDAQ 11.0 installed at a
      directory in your PATH. If you have not already done so, do the following
      before continuing:

```
spdaqxx> unset DAQROOT
spdaqxx> source /usr/opt/nscldaq/11.0/daqsetup.bash
spdaqxx> export PATH=$DAQBIN:$PATH
    
```

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| The full SpecTcl program. | Up | The electronics |
