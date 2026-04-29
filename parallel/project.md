|  |  |  |
| --- | --- | --- |
| mpiSpecTcl. |
| Prev |  | Next |


---

# <a name="AEN1656"></a>project

<a name="AEN1660"></a>## Name

project -- Create projection spectra

<a name="AEN1663"></a>## Synopsis

**project**  [`[no]snapshot`]  *sourcde-spectrum* *new-spectrum*   
                         [x | y]
                      [displayable-contour]

<a name="AEN1678"></a>## DESCRIPTION

This command is wrapped in a 
                    `CMPITclCommand`.  It can only be executed in the
                    MPI_EVENT_SINK_RANK as that's the only rank that has, not only
                    a spectrum  dictionary but access to spectrum channels.  All other processes
                    return TCL_OK and no result.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| pman | Up | pseudo |
