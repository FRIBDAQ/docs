|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="chapter.scalerdisplay"></a>Chapter 23. Scaler Display Software.

The scaler display software consists of two components:



[[r8051]]Connects to the NSCL data acquisition system buffer manager
                        and accepts scaler and run state-change buffers.  The software
                        connects to a
                        [[r10588]]
                        application and maintains a set of Tcl variables in that server
                        that describe instantaneous and continuous scaler state.

[[r10722]]A script that starts up a
                        [[r10588]] that runs a script
                        which takes the variables maintained by
                        [[r8051]], a configuration file
                        and produces a scaler display.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Theringselectorapplication | Up | The Scaler Display Client |
