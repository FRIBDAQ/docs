|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="CVMEStatusModule"></a>CVMEStatusModule

<a name="AEN49677"></a>## Name

CVMEStatusModule -- Implement a status module using the CAEN V262 module.

<a name="AEN49680"></a>## Synopsis

```
#include <CVMEStatusModule.h>
            
```

```
  CVMEStatusModule(UInt_t base, int crate = 0);
```

<a name="AEN49711"></a>## Description

Implements a concrete status class for the CAEN V262 I/O module.  While this
                module is no longer in the CAEN catalog, the NSCL has quite a few of them and
                we do not *yet* discourage its use.  The CAENV V977 module is
                one alternative to this device.

See also the `CVMETrigger` class that uses this module
                as a trigger module.

<a name="AEN49717"></a>## Public member functions

`  CVMEStatusModule(UInt_t base, int crate = 0);`Constructs a status module based on the CAEN V262.  The V262 has a base address
                of `base` set in its rotary switches and lives in
                VME crate `crate`, which defaults to crate 0 if not supplied.
                The default is correct for a single crate system.

`  CVMEStatusModule(const CCaenIO& module);`Constructs a VME status module given a pre-existing CAEN V262 object
                (`CCaenIO`).

` virtual   void GoBusy();`The status module indicates the system is unable to accept triggers
                by pulsing the SHP 0 output.

` virtual   void GoClear();`The status module indicates the system is now able to accept triggers
                after going dead (either due to a trigger or a call to `GoBusy`)
                by pulsing SHP 1.

` virtual   void ModuleClear();`Indicates the modules can be cleared by pulsing SHP 3.
                This can be fanned out into modules with external clears.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CVMEScalerLRS1151 | Up | CVMETrigger |
