|  |  |  |
| --- | --- | --- |
| SpecTcl Sqlite3 interfaces |
| Prev |  | Next |


---

# <a name="AEN79"></a>dbconfig::makeSchema

<a name="AEN83"></a>## Name

dbconfig::makeSchema -- Create database schema

<a name="AEN86"></a>## Synopsis

**                        package require dbconfig
                    **   
**                        sqlite3 *dbcommand filename*
**   
**                        dbconfig::makeSchema *dbcommand*
**

<a name="AEN93"></a>## DESCRIPTION

The **makeSchema** command
                        creates the database schema into a database file.
                        Before a database file can be used it must have
                        a schema definition created.  This definition
                        defines tables and indices (structures
                        that improve the performance of specific
                        queries).

The synopsis shows an sqlite connection being
                        established to a database file (presumably new)
                        and the schema being defined in that file.
                        Note that the schema are defined in a non-
                        destructive manner.  It's therefore safe for
                        this to be called on a file that already
                        contains data.

It is a good idea to invoke this if you open a database
                        you intend to write to even if you know the scheme are
                        already defined.  Tables are defined using
                        CREATE TABLE IF NOT EXISTS ... so
                        redefinitions are harmless.  Making the schema again
                        will create any  new tables that have been added to the
                        standard schema since the last use.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| The Tcl API | Up | dbconfig::saveConfig |
