|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="daq1.lg_create"></a>lg_create

<a name="AEN20641"></a>## Name

lg_create -- Create a new logbook database.

<a name="AEN20644"></a>## Synopsis

**lg_create `-filename` file [`-current` *bool*]
   [`-experiment` *experiment-id*]
   [`-spokesperson` *experiment-spokesperson*]
   [`-purpose` *experiment-purpose*]
         **

<a name="AEN20660"></a>## DESCRIPTION

**lg_create** creates a new logbook database file.
            The `-filename` is mandatory and is used to provide
            the name of a file to create.  It is an error to attempt to create
            a logbook into an existing file.  The remaining options are
            optional.  With the exception of `-current` they
            provide information about the logbook that will be put in the
            database's key value store.

`-current` requires a boolean parameter.  If this
            parameter is true, after creating the logbook, it is made the current
            logbook.  Boolean values can be any legal Tcl boolean value.

The key value options are:



`-experiment`Provides the experiment ID. This is normally assigned by
                     the facility at which the experiment is run.  The value
                     of this option will be stored as the key
                     experiment.

`-spokesperson`Provides the experiment's spokesperson.  This value is stored
                     in the spokesperson key of the database's
                     key value store.

`-purpose`Provides a brief description of the purpose of the experiment.
                     This must be quoted if there are any white-space characters.

If any of the experiment description parameters are omitted,
            the **lg_create** command will switch into GUI
            mode and display a dialog form that allows you to fill in the
            remaining parameters.  All of the above parameters are mandatory this
            facility is just provided to make the command line a bit less
            unwieldy.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| evbwizard | Up | lg_current |
