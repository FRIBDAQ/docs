|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="daq1.lg_addperson"></a>lg_addperson

<a name="AEN17969"></a>## Name

lg_addperson -- Add a person to the logbook.

<a name="AEN17972"></a>## Synopsis

**lg_addperson [ *lastname firstname*
   [*salutation*]
]
         **

<a name="AEN17979"></a>## DESCRIPTION

Since experiments are staffed by people and artifacts in the logbook
            are associated with people, the people that can create artifacts
            must be made known to the database. This command adds a person
            to the database.

A person is identified by their `lastname`,
            `firstname` and an optional
            `salutation`.

If none of these are provided to the command, it switches to GUI
            mode and pops up a dialog box that allows people to be added to the
            database.  The dialog provides entries for the three fields that
            define a person (salutation can be left blank).  The
            Add button adds the person described and the
            Done button exits the dialog.
            Thus GUI Mode allows more than one person to be added in a
            single invocation of the command.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| lg_ls | Up | lg_lspeople |
