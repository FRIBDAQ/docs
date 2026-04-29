|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="daq1_vmusbloader"></a>vmusbloader

<a name="AEN14445"></a>## Name

vmusbloader -- VM-USB Firmware loader

<a name="AEN14448"></a>## Synopsis

**vmusbloader *firmware-filename [serial-string]*
**

<a name="AEN14453"></a>## DESCRIPTION

Loads the firmware-filename into the currently
            selected firmware location. See
            [[c7843]]
            for the full load procedure.

If *serial-string* is provided it must be
            a serial number string for a powered up device attached to the system.
            The VM-USB with that serial number will be used.

<a name="AEN14460"></a>## KNOWN ISSUES

The format of firmware files does not match the documentation available.
            For .bit files it is necessary to skip headers to get to the load
            data.  If you have bit files that are not loadable report this problem
            and use the corresponding .bin file instead.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| ccusbloader | Up | ringselector |
