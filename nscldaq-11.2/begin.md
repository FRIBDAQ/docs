|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="provider3_begin"></a>begin

<a name="AEN59359"></a>## Name

begin -- Start data taking in a data source

<a name="AEN59362"></a>## Synopsis

**proc ::*providerName*::begin {sourceId runNumber title} {
...
}
          **

<a name="AEN59366"></a>## DESCRIPTION

Starts data taking at the beginning of a run for the
            source identified by `sourceId`.  The
            `runNumber` and `title`
            parameters are the run number and title of the run.  They
            can be ignored if the data source has specified that it does not
            have the capability of associatig run numbers and titles with
            data taking runs.

The `sourceId` parameter is, as usual,
            the value of the sourceid dict element passed to the
            [[r59253]]
            command.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| stop | Up | pause |
