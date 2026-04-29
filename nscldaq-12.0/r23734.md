|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="evb1_reset"></a>EVB::reset

<a name="AEN23748"></a>## Name

EVB::reset -- Reset timestamp clocks.

<a name="AEN23751"></a>## Synopsis

**EVB::reset
          **

<a name="AEN23754"></a>## DESCRIPTION

Resets the event builder's timing information as if it had just been
            started.  If you are using the system with a system that resets
            timestamps back to near zero at the start of each data taking, you
            can use this to prevent an initial set of out of order packet errors.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| EVB::flush | Up | 1tcl |
