|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN6568"></a>Chapter 12. 
    Mesytec MCFD-16 Controls

# <a name="AEN6570"></a>12.1. Overview

The Mesytec MCFD-16 is a 16-channel discriminator in the NIM form factor.
      Configuration of the device can be performed remotely over different
      communication protocols: usb and RC-bus. A GUI called MCFD16Control is
      provided as a part of NSCLDAQ to support communication with the device through both these
      protocols. A key feature is the ability to
      generate a tcl script capable of configuring the device with the same
      settings displayed in the GUI.

The parameters that the GUI provides control over are the threshold,
      gain, width, dead time, delay, constant fraction, and polarity. All of
      these parameters
      can be set individually or commonly depending on the mode setting selected
      in the GUI. The interface reflects whether or not the device is being
      configured in either of these modes and prevents the setting of individual
      settings while in common mode. Doing so may not succeed and is therefore
      protected against. Finally, the GUI provides
      the ability to enable and disable channel pairs and to control the
      pulser.

It is important to know that the two different protocols sometimes accept different value
      ranges for the same parameter. One can see this by reading the manual
      and comparing the different ranges accepted for the gain setting in USB
      and RC-bus. To provide a unified user experience,
      the RC-bus ranges were chosen over the USB so if the user wants to refer
      to the manual, he/she should refer to the RC-bus section rather than the
      USB section.

Finally, the control provided over the MCFD-16 through the GUI is made
      available through low-level drivers that can be used in any tclsh. The
      user can incorporate calls to these drivers in any script they want and
      can build input files to load into the GUI if desired.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| device-support | Up | Starting the GUI for USB communication |
