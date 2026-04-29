|  |  |  |
| --- | --- | --- |
| mpiSpecTcl. |
| Prev |  | Next |


---

# <a name="AEN1734"></a>ringformat

<a name="AEN1738"></a>## Name

ringformat -- Set the ring buffer fallback format version

<a name="AEN1741"></a>## Synopsis

**ringformat** *major*.*minor*

<a name="AEN1747"></a>## DESCRIPTION

Sets the ring format version to use in the event there is no ring version ring item
                    in the data stream.  As this only matters for the data source, the command is not
                    encapsulated and is only effective when used in MPI_ROOT_RANK.
                    In practice, this is not a restriction as typically, this command is issued by
                    scripts running in the MPI_ROOT_RANK process.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| remote | Up | sbind |
