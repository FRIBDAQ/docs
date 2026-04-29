|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="usbloaders_chap"></a>Chapter 27. VM/CCUSB Firmware loaders

The VM-USB and CC-USB main Xilinx FPGA chips load their configuration
        from an EEPROM.  The EEPROM can be programmed over the USB interface.
        The [[r12936]]
        and [[r12970]]
        programs provided by and redistributed with the permission of Wiener-Plein
        Baus are programs that program the FPGA load EEPROMS.

These loaders work both with Xilinx .bit and
        .bin files.

The XX-USB devices have four load locations. Which one runs and which
        one is programmed is selected by the rotary switch on the XX-USB front panel.

**XX-USB load procedure**

1. Select a program location (1-4) by pointing to the appropriate
               P1,2,3,4 location with the front panel rotary switch.
2. Run the appropriate loader as per the documentation in the
                   reference section linked to above.
3. Select the run location of the firmware by selecting the
                   appropriate C1,2,3,4 location with the rotary switch
4. Double check that the device will start that firmware by
                   cycling power on the VME/CAMAC crate.

Once you have checked that the firmware performs as expected,
        you can program all firmware locations by following the above procedure
        three more times selecting different P locations until all have been
        programmed.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Sample programs that use the package | Up | xlmload firmware loader for XLM modules via VM-USB controllers. |
