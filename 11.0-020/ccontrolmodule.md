|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="ccusb3-ccontrolmodule"></a>CControlModule

<a name="AEN51467"></a>## Name

CControlModule -- Configuration and wrapper for CControlHardware

<a name="AEN51470"></a>## Synopsis

```
CControlModule : public CConfigurableObject
```

<a name="AEN51526"></a>## DESCRIPTION

`CControlModule` objects serve a dual purpose.
            On the one hand, the methods supplied by them wrap the
            driver objects (
            [[r51243]]
            derived objects).
            On the other hand, by inheriting from
            [[r48859]], this object
            provides a configuration database for those driver object.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CControlHardware | Up | CCCUSBControl |
