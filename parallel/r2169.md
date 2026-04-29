|  |  |  |
| --- | --- | --- |
| mpiSpecTcl. |
| Prev |  | Next |


---

# <a name="AEN2169"></a>unbind

<a name="AEN2173"></a>## Name

unbind -- Unbind spectra from display shared memory

<a name="AEN2176"></a>## Synopsis

**unbind** *spectrum-name*...

**unbind** `-id` *id*...

**unbind** `-all`

<a name="AEN2191"></a>## DESCRIPTION

This command is part of the spectrum command package 
                    (`CSpectrumPackage`).  It is wrapped in a 
                    `CMPITclPackagedCommand`.  It only runs in the 
                    MPI_EVENT_SINK_RANK   since that is the rank that
                    creates and maintains the display shared memory and histogram data 
                    that are manipulated by **unbind**.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| treevariable | Up | ungate |
