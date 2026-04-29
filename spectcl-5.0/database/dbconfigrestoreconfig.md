|  |  |  |
| --- | --- | --- |
| SpecTcl Sqlite3 interfaces |
| Prev |  | Next |


---

# <a name="AEN6131"></a>dbconfig::restoreConfig

<a name="AEN6135"></a>## Name

dbconfig::restoreConfig -- Restore analysis configuration from saveset

<a name="AEN6138"></a>## Synopsis

```
package require dbconfig
set db [dbconfig::connect file-name]

dbconfig::restoreConfig $db save-name ?restorespectra?

                        
```

<a name="AEN6140"></a>## DESCRIPTION

Restores an analysis configuration from the save set
                            named `save-name`.
                            `db` is a database connected.
                            If `restorespectra` is provided
                            and true, all saved spectrum channels are restored
                            as well.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| dbconfig::listConfigs | Up | dbconfig::saveSpectrum |
