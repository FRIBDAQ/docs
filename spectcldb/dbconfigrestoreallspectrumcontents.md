|  |  |  |
| --- | --- | --- |
| SpecTcl Sqlite3 interfaces |
| Prev |  | Next |


---

# <a name="AEN6188"></a>dbconfig::restoreAllSpectrumContents

<a name="AEN6192"></a>## Name

dbconfig::restoreAllSpectrumContents -- Load channels for all spectra

<a name="AEN6195"></a>## Synopsis

```
package require dbconfig
set db [dbconfig::connect file-name]
set set [dbconfig::openSaveSet $db set-name]

dbconfig::restoreAllSpectrumContents $set
                        
```

<a name="AEN6197"></a>## DESCRIPTION

Given a save set instance command
                            `$set`, load the
                            channel data from all spectra stored in that
                            saveset into SpecTcl spectra.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| dbconfig::saveAllSpectrumContents | Up | dbconfig::listRuns |
