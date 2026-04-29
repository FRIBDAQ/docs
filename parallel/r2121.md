|  |  |  |
| --- | --- | --- |
| mpiSpecTcl. |
| Prev |  | Next |


---

# <a name="AEN2121"></a>treevariable

<a name="AEN2125"></a>## Name

treevariable -- Manipulate Tree variables

<a name="AEN2128"></a>## Synopsis

**treevariable** `-list`  [*glob-name-pattern*]

**treevariable** `-set` *name* *value*  [*units-of-measure*]

**treevariable** `-check` *name*

**treevariable** `-setchanged` *name*

**treevariable** `-firetraces`  [*glob-pattern*]

<a name="AEN2163"></a>## DESCRIPTION

This command is wrapped in a `CMPITclCommandAll`.
                    Tree variables, in practice, steer computations in the event processing
                    pipeline. Furthermore, it is typically the event processing pipeline
                    elements that construct a treevariable.  Therfore, if the rank of the
                    process is less than MPI_FIRST_WORKER_RANK the command
                    simply returns TCL_OK and no result.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| treeparameter | Up | unbind |
