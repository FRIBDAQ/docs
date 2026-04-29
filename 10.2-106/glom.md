|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="daq1_glom"></a>glom

<a name="AEN6944"></a>## Name

glom -- Glue event fragments together into events

<a name="AEN6947"></a>## Synopsis

**glom *options*
**

<a name="AEN6951"></a>## DESCRIPTION

Glom is a filter that accepts event ordered event fragments on stdin
            and emits event ring items on standard output.  Event fragments that
            represent non physics triggers are just passed through, with the
            event fragment header stripped off so that they become their initial
            ring items again.

Any errors glom wants to complain about are emitted to its standard
            error.  It is therefore normally a bad idea to have glom's standard
            output and standard error pointed to the same sink.
            Glom's behavior is controlled by command line options that are
            documented in OPTIONS below.

<a name="AEN6956"></a>## OPTIONS



`--nobuild`If this option is present, glom won't attempt to glue
                            together event fragments, but will emit each event fragment
                            as a single vent.

`--dt` *ticks*This mandatory parameter provides the number of
                            timestamp ticks that define a coincidence interval
                            when building events.  The value of *ticks*
                            is ignored but currently necessary when `--nobuild`
                            is speicified.

<a name="AEN6972"></a>## KNOWN ISSUES



1. `--dt` should probably not be necessary if
                       `--nobuild` is present.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| frag2ring | Up | S800 Ring fragment data source |
