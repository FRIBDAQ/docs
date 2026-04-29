|  |  |  |
| --- | --- | --- |
| SpecTcl Sqlite3 interfaces |
| Prev |  | Next |


---

# <a name="AEN309"></a>dbconfig::listSavedSpectra

<a name="AEN313"></a>## Name

dbconfig::listSavedSpectra --

<a name="AEN316"></a>## Synopsis

**package require dbconfig
                    **   
**sqlite3 *db some-file*
**   
**set list [dbconfig::listSavedSpectra *db save-set*]
                    **

<a name="AEN323"></a>## DESCRIPTION

Returns a list of the spectra that are in a
                     save set.  `db` is the
                     database connection command created by
                     **sqlite3** command.
                     `save-set` is the name of the
                     save-set to list saved spectra from.

<a name="AEN329"></a>## EXAMPLES

<a name="AEN331"></a>```
package require dbconfig
package require Tk
sqlite3 db test.db
set savedSpectra [dbconfig::listSavedSpectra db withsomespec]
toplevel .restore
set i 1
foreach spectrum $savedSpectra {
    button .restore.b$i -text $spectrum \
      -command [list dbconfig::restoreSpectrum db withsomespec $spectrum]
    pack .restore.b$i
    incr i
}
                    
```

This example, creates a new top-level that contains
                    a button for each spectrum in the
                    withsomespec save set in the
                    database test.db.  Each
                    button is labeled with a spectrum and programmed
                    to restore the contents of that spectrum.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| dbconfig::restoreAllSpectrumContents | Up | dbconfig::listRuns |
