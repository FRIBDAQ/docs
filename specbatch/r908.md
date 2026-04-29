|  |  |  |
| --- | --- | --- |
| Batch SpecTcl (5.2 and later) |
| Prev |  |  |


---

# <a name="AEN908"></a>mpisink

<a name="AEN912"></a>## Name

mpisink -- Send data to MPI getters.

<a name="AEN915"></a>## Synopsis

**package require mpispectcl
                        **

**mpisink
                        **

<a name="AEN920"></a>## DESCRIPTION

Establishes a batch data distributor to distribute
                        to one or more ranks that are running an MPI data getter
                        (established via **mpisource**).
                        The sink knows which ranks to send data to because the
                        protocol used is a pull protocol that requires ranks
                        to request data prior to receiving it.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home |  |
| mpisource | Up |  |
