|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="ccusb3-ccontrolmodule"></a>CControlModule

<a name="AEN79874"></a>## Name

CControlModule -- Configuration and wrapper for CControlHardware

<a name="AEN79877"></a>## Synopsis

```
CControlModule : public CConfigurableObject
```

<a name="AEN79933"></a>## DESCRIPTION

`CControlModule` objects serve a dual purpose.
            On the one hand, the methods supplied by them wrap the
            driver objects (
            [[r79630]]
            derived objects).
            On the other hand, by inheriting from
            [[r77196]], this object
            provides a configuration database for those driver object.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CControlHardware | Up | CCCUSBControl |
