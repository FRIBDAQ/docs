|  |  |  |
| --- | --- | --- |
| SpecTcl Sqlite3 interfaces |
| Prev |  | Next |


---

# <a name="AEN6175"></a>dbconfig::saveAllSpectrumContents

<a name="AEN6179"></a>## Name

dbconfig::saveAllSpectrumContents -- Save the contents of all spectra to a saveset

<a name="AEN6182"></a>## Synopsis

```
package require dbconfig
set db [dbconfig::connect file-name]
set set [dbconfig::openSaveSet $db set-name]
 
dbconfig::saveAllSpectrumContents $set 
                        
```

<a name="AEN6184"></a>## DESCRIPTION

Given a saveset handle `set`,
                            saves the contents of all spectra into that saveset.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| dbconfig::restoreSpectrum | Up | dbconfig::restoreAllSpectrumContents |
