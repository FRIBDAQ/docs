|  |  |  |
| --- | --- | --- |
| mpiSpecTcl. |
| Prev |  | Next |


---

# <a name="AEN1265"></a>evbunpack

<a name="AEN1269"></a>## Name

evbunpack -- mpiSpecTcl implementation of evbunpack

<a name="AEN1272"></a>## Synopsis

**evbunpack create** *name* *clock-MHz* *diagnostic-parameter-base-names*

**evbunpack addprocessor** *processor-name* *source-id* *pipeline-name*

**evbunpack list**  [*pattern*]

<a name="AEN1293"></a>## DESCRIPTION

This command controls the manipulation of event builder event processors.
                    It is encapsulated in a `CMPITclCommand`.  In fact, however,
                    only the analysis pipelines an event builder event processors defined in the
                    worker processes (rank >= MPI_FIRST_WORKER_RANK) matter 
                    as those processes are the ones that run the event processing pipeline.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| clear | Up | filter |
