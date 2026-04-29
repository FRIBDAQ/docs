|  |  |  |
| --- | --- | --- |
| mpiSpecTcl. |
| Prev |  | Next |


---

# <a name="AEN1108"></a>applygate

<a name="AEN1112"></a>## Name

applygate -- Apply a gate to one or more spectra

<a name="AEN1115"></a>## Synopsis

**applygate** *gate-name* *spectrum-name*...

**applygate** `-list` *[pattern]*

<a name="AEN1129"></a>## DESCRIPTION

This commands replaces the **apply** command in prior
                    versions of SpecTcl. This replacement was done because the 
                    **apply** command was added to the Tcl core command
                    set in version 8.5 and by now there are Tcl packages and scripts internal
                    to the Tcl implementation that rely on that command and fail if SpecTcl
                    overrides it.

The implementation of the **applygate** command is wrapped in
                    a `CMPITclPackagedCommand`.

Ultimately the SpecTcl
                    API is used to perform gate applications.    If there is a histogrammer object, as there
                    is in the MPI_EVENT_SINK_RANK it is used to apply the gate.  If not,
                    the spectrum is looked up in the mirrored spectrum dictionary and asked to apply the gate.

When listing gates;  this command only operates in the MPI_EVENT_SINK_RANK
                    process.  It enumerates spectra that match the optional *pattern*
                    (which defaults to * matching all spectra).  Each spectrum is asked
                    about the gate applied to it and returns the list as the result with a status of 
                    TCL_OK.  All other ranks return a status of TCL_OK
                    but an empty result. Since the overall command result is the longest of all resuts, the
                    gate application list is the ultimate result of the command.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| SpecTcl commands in the mpiSpecTcl environment | Up | attach |
