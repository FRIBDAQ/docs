|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="evb1_barriertrace"></a>EVB::barriertrace

<a name="AEN14984"></a>## Name

EVB::barriertrace -- Supply a script to invoke on barrier events.

<a name="AEN14987"></a>## Synopsis

**EVB::barriertrace complete ?*script*?
          **

**EVB::barriertrace incomplete ?*script*?
                **

<a name="AEN14994"></a>## DESCRIPTION

The first form of this command places, deletes or lists the script
            that is associated with properly formed barrier events.
            If a script is not supplied, the current script is returned.  If there
            is no current script an emtpy string is returned.
            If a script is supplied it replaces the current complete barrier
            script. If an empty string is supplied for the new script, no script
            will be called for future complete barriers.

Complete barrier scripts have appended to them a list of pairs. Each
            pair contains the source Id of a barrier contributor and the
            type of barrier event emitted by that source.

The second form of this command performs the same function for
            incomplete barriers.  An incomplete barrier is one for which barrier
            fragments have not been received from all sources within a timeout
            period.

Incomplete barrier scripts receives two additional parameters. The
            first additional parameter is identical to the parameter
            passed to complete barrier scripts.  The second additional parameter
            is a list of data source ids that did not emit a barrier fragment
            prior to the barrier timeout.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| EVB::onDataLate | Up | EVB::source |
