|  |  |  |
| --- | --- | --- |
| SpecTcl Sqlite3 interfaces |
| Prev |  | Next |


---

# <a name="AEN6256"></a>dbconfig::getRunInfo

<a name="AEN6260"></a>## Name

dbconfig::getRunInfo -- Get information about all runs in a saveset.

<a name="AEN6263"></a>## Synopsis

```
package require dbconfig
set db [dbconfig::connect file-name]
set set [dbconfig::openSaveSet $db set-name]

set info [dbconfig::getRunInfo $set]
                        
```

<a name="AEN6265"></a>## DESCRIPTION

Returns a list of dicts that describe all of the
                            runs in a save set.  If there are no runs,
                            an empty list is returned.  See
                            **dbconfig::listRuns**
                            for the keys each dict will have.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| dbconfig::hasRun | Up | dbconfig::getScalers |
