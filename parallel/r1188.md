|  |  |  |
| --- | --- | --- |
| mpiSpecTcl. |
| Prev |  | Next |


---

# <a name="AEN1188"></a>channel

<a name="AEN1192"></a>## Name

channel -- Describe mpiSpecTcl implementation of the channel command.

<a name="AEN1195"></a>## Synopsis

**channel** `-set` *spectrum-name* *channel-indices* *new-value*

**channel** `-get` *spectrum-name* *channel-indices*

<a name="AEN1214"></a>## DESCRIPTION

This command is encapsulated in a `CMPITclPackagedCommand`.
                    It only actually does something if the process has a histogrammer, and that's
                    currently only MPI_EVENT_SINK_RANK  In all other processes,
                    this command is a no-op that does not set the result and returns 
                    TCL_OK as its status.  Thus in the `-get`,
                    since the non empty MPI_EVENT_SINK_RANK result will be the 
                    longest, it will be the command result, which is correct.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| attach | Up | clear |
