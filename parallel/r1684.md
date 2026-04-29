|  |  |  |
| --- | --- | --- |
| mpiSpecTcl. |
| Prev |  | Next |


---

# <a name="AEN1684"></a>pseudo

<a name="AEN1688"></a>## Name

pseudo -- Create and manipulate pseudo parameters

<a name="AEN1691"></a>## Synopsis

**pseudo** *name* *dependent-parameter-tcl-list* *tcl-proc-body*

**pseudo** `-list`  [ choice='opt'>*glob-pattern*]

**pseudo** `-delete` *name*...

<a name="AEN1712"></a>## DESCRIPTION

This is encapsulated in a `CMPITclPackagedCommand`
                    as it is part of the parameter package of commands.  It only executes in the
                    event sink pipeline as pseudo parameters are computed when all ordinary
                    parameters have been computed as a step in the event sink pipeline prior to 
                    actual histograming.  All other processes return  TCL_OK
                    and an empty result.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| project | Up | remote |
