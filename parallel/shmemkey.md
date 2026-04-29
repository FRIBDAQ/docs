|  |  |  |
| --- | --- | --- |
| mpiSpecTcl. |
| Prev |  | Next |


---

# <a name="AEN1791"></a>shmemkey

<a name="AEN1795"></a>## Name

shmemkey -- Provide display shared memory identification

<a name="AEN1798"></a>## Synopsis

**shmemkey**

<a name="AEN1801"></a>## DESCRITPION

This command is wrapped in a `CMPITclCOmmand`.
                    The display shared memory is created and maintained by MPI_EVENT_SINK_RANK.
                    In all processes but that one, the command returns a status of TCL_OK
                    and an empty result.  On the MPI_EVENT_SINK_RANK, the shared memory
                    identification is set as the command result and TCL_OK returned as the
                    status.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| sbind | Up | shmemsize |
