|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="daq1.lg_current"></a>lg_current

<a name="AEN21696"></a>## Name

lg_current -- Set the current logbook database

<a name="AEN21699"></a>## Synopsis

**lg_create [*databasefile*]
         **

<a name="AEN21704"></a>## DESCRIPTION

Sets the current datadatabase for the other
            **lg_*** commands and for the Tcl logbook high level
            interface.  If `databasefile` is not provided,
            the command switches to GUI mode and prompts for it.

<a name="AEN21709"></a>## FILES



~/.nscl-logbook-currentThe logbook selected is written into this file and this is
                  then used in subsequente **lg_***
                  commands as the current database file.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| lg_create | Up | lg_ls |
