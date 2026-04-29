|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="daq1_teering"></a>teering

<a name="AEN7055"></a>## Name

teering -- Tee data to stdout and a ringbuffer.

<a name="AEN7058"></a>## Synopsis

**teering --ring=*ring-name*
**

<a name="AEN7062"></a>## DESCRIPTION

teering is similar to the Unix
            tee program.  Where
            tee takes its standard input and
            outputs it to a file as well as its standard output,
            teeringtakes as input ringbuffer items,
            and outputs them both to a ring buffer and standard output.

The intent of teering is to provide
            you with the ability to create test points along the path of a
            pipeline that transforms data from one set of ring items to another.
            A sample use of teering is to provide a test point for the ordered
            event fragments emitted from the event orderer before
            glom is used to build events.

teering has a single command option
            that is required: `--ring`'s argument provides the
            name of the ring into which teering will
            output data.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| S800 Ring fragment data source | Up | Readout Gui |
