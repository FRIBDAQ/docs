|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN8992"></a>Chapter 17. 
    Mesytec MSCF-16 Controls

# <a name="AEN8994"></a>17.1. Overview

The Mesytec MSCF-16 is a 16-channel shaping amplifier with CFD.
      The device can be remotely controlled via either USB or Mesytec's RC-bus.
      A GUI called MCFD16Control is provided as a part of NSCLDAQ to control the
      device through the USB protocol only. 
      A key feature is the ability to
      generate a tcl script capable of configuring the device with the same
      settings displayed in the GUI.

The parameters that the GUI provides control over are the threshold,
      gain, pole zero, shaping time, configuration mode, remote control mode,
      and also monitor channel.  All of these 
      can be set individually or commonly depending on the mode setting selected
      in the GUI. The interface reflects whether or not the device is being
      configured in either of these modes and prevents the setting of individual
      settings while in common mode.

Finally, the control provided over the MSCF-16 through the GUI is made
      available through low-level drivers that can be used in any tclsh. The
      user can incorporate calls to these drivers in any script they want and
      can build input files to load into the GUI if desired.  In the same
      manner, if the user is in need of control of the device through the
      RC-bus, there is primitive support for communicating with a device through
      a digitizer in the MxDC family in VMUSBReadout. The user can then make the
      low level calls through the MXDCRCProxy snit::type.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Saving and restoring state | Up | Synchronization Paradigm |
