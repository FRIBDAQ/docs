|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="provider3_pause"></a>pause

<a name="AEN82598"></a>## Name

pause -- Pause a data taking run (optional)

<a name="AEN82601"></a>## Synopsis

**proc ::*providerName*::pause *sourceId* {
...
}
          **

<a name="AEN82606"></a>## DESCRIPTION

Pauses a data taking run in the data source identified by
            `sourceId`.
            The `sourceId` parameter is
            the value of the sourceid dict element passed to the
            [[r82461]]
            command.

This proc is optional.  Specifically, if the data source provider's
            [[r82712]] specifies  the
            provider is unable to pause runs, the provider need not implement
            either this proc or the
            [[r82621]]
            proc.  Similarly, the data source manager should not invoke the
            **pause** or **resume** commands on
            data sources that cannot support it.

The ReadoutGUI data source manager and GUI will prevent an invocation
            of the **pause** and **resume**
            operations on any data of the data sources
            unless all data sources specified able to perform these
            operations.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| begin | Up | resume |
