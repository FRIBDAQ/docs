|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN20478"></a>mg_import

<a name="AEN20482"></a>## Name

mg_import -- Import an experiment definition

<a name="AEN20485"></a>## Synopsis

**$DAQBIN/mg_import *def-to-import  prefix target-definition*
**

<a name="AEN20489"></a>## DESCRIPTION

This command imports the experiment definition in the configuration database file
         `def-to-import`  into the target experiment configuration database file
         `target-definition`.   All names (containers, programs, spequencdes e.g.) are
         prefixed with the `prefix` followed by a hyphen.  For example, if 
         `def-to-import` defines a container named bustesr and
         `prefix`  is s800  that container will be imported as
         s800-buster.  Note that in the example, references to the buster
         container will be modified to referencdes to s800-buster and so on.

The renaming described in the previous paragraph is done to ensure there are no duplicate names in 
         `target-definition` after the import.
         There is one case where this cannot be done.   Eventloggers are not named, but their target directories
         must be unique (two event loggers are not allowed to log to the same directory (tree)).
         If an event logger would conflict in that way with one already defined in `target-definition`
         it is not imported and an error message is emitted to stderr.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| mg_program_wizard | Up | ReadoutShell |
