|  |  |  |
| --- | --- | --- |
| mpiSpecTcl. |
| Prev |  | Next |


---

# <a name="AEN1492"></a>integrate

<a name="AEN1496"></a>## Name

integrate -- Integrate an area of interest

<a name="AEN1499"></a>## Synopsis

**integerate** *spectrum-name* *area-of-interest*

<a name="AEN1506"></a>## DESCRPTION

Integrates an area of interest within a specific spectrum named
                    *spectrum-name* the *area-of-interest*
                    can either be spectrum coordinates or a displayable gate.

The command is wrapped in a `CMPITclCommand`.
                    This command is only executed in the MPI_EVENT_SINK_RANK process,
                    as it is the only one with access to spectrum channel values as well as definitions.
                    In all other processes, a status of TCL_OK is returned and
                    an empty result is produced.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| gate | Up | mirror |
