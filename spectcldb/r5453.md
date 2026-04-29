|  |  |  |
| --- | --- | --- |
| SpecTcl Sqlite3 interfaces |
| Prev |  | Next |


---

# <a name="AEN5453"></a>DBTcl

<a name="AEN5457"></a>## Name

DBTcl -- Provide database access.

<a name="AEN5460"></a>## Synopsis

```
package require SpecTclDB ?1.0?

DBTcl create filename
set instance [DBTcl connect filename]

                        
```

<a name="AEN5462"></a>## DESCRIPTION

The **DBTcl** command
                            has two subcommands:



**create**Accepts a filename as an argument.
                                    If the file specified does not exist,
                                    it is created.  Regardless the file
                                    is opened as an SQLite3 database and
                                    the schema needed to store savesets
                                    and their objects created.

**connect**Accepts a filename as an argument. The
                                    file is opened as an
                                    SQLite3 database and tests are done to
                                    ensure that appropriate schema are present.
                                    A database instance command is generated
                                    (see the
                                    Database Instance
                                    reference page) and returned
                                    as the value of the command.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Tcl bindings to the C++ API | Up | Database Instance |
