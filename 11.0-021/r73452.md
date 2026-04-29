|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.cv977busy"></a>CV977Busy

<a name="AEN73456"></a>## Name

CV977Busy -- Concrete busy class using the CAEN V977 module

<a name="AEN73459"></a>## Synopsis

```
#include <CV977Busy.h>
         
```

```
  CV977Busy(uint32_t base, unsigned crate = 0);
```

<a name="AEN73488"></a>## Description

Busy objects control external hardware that indicates when the readout
            software is unable to respond to a new trigger.   The CAENV977 module
            achieves this by using its ability to copy input signals to it's outputs
            in a latchemd manner.  It is legal to use a single module as both a
            trigger and a busy module.

The following signals are used by the module:

<a name="AEN73492"></a>| Plug | Direction | Meaning |
| --- | --- | --- |
| 0 | Input (left) | This should be the event trigger the computer sees.
                                This is the trgger input as well for when the
                                module is being used as a trigger. |
| 0 | Output (right) | Computer is busy. |
| 1 | Output (right) | Computer going busy for software reasons (pulsed) |

<a name="AEN73513"></a>## Public member functions

`  CV977Busy(uint32_t base, unsigned crate = 0);`Constructor that uses the `base` address
                and VME `crate` number to describe the
                module.

`  CV977Busy(CCAENV977& module);`Constructor that operates with an existing
                `CCAENV977` `module`.

` virtual void GoBusy();`Called by the framework to pulse the going busy output.

` virtual void GoClear();`Called by the framework to clear the busy output.

<a name="AEN73549"></a>## SEE ALSO

[[r71413]],
     [[r73554]]

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CTimedTrigger | Up | CV977Trigger |
