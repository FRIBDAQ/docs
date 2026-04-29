|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="evb1_flush"></a>EVB::flush

<a name="AEN15298"></a>## Name

EVB::flush -- Empty all input queues.

<a name="AEN15301"></a>## Synopsis

**EVB::flush
          **

<a name="AEN15304"></a>## DESCRIPTION

The fragments in all input queues are flushed to output in timestamp
            order.  All observers on the output of fragments are invoked which
            ensures that output statistics are maintained and that the fragments
            make their way to the orderer's output stage.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| EVB::reviveSocket | Up | EVB::reset |
