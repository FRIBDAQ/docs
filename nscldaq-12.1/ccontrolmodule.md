|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="ccusb3-ccontrolmodule"></a>CControlModule

<a name="AEN78389"></a>## Name

CControlModule -- Configuration and wrapper for CControlHardware

<a name="AEN78392"></a>## Synopsis

```
CControlModule : public CConfigurableObject
```

<a name="AEN78448"></a>## DESCRIPTION

`CControlModule` objects serve a dual purpose.
            On the one hand, the methods supplied by them wrap the
            driver objects (
            [[r78145]]
            derived objects).
            On the other hand, by inheriting from
            [[r75711]], this object
            provides a configuration database for those driver object.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CControlHardware | Up | CCCUSBControl |
