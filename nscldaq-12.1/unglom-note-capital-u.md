|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN22471"></a>Unglom (note capital U)

<a name="AEN22475"></a>## Name

Unglom (note captital U) -- Break up event file into fragment flie

<a name="AEN22478"></a>## Synopsis

**$DAQBIN/Unglom *source-URI*
**

<a name="AEN22482"></a>## DESCRIPTION

This command (not to be confused with
            **unglom** which you probably should be
            using instead), takes an event file that has been through
            the FRIB event builder and breaks it up into event files
            containing the fragments from each event.  Each source Id
            in the input event file will produce an output file named
            sid-*source-id*
            with the fragments from that source id.  These files will
            be written in the current working directory.

For example, suppose your events are built from sources
            with ids 1,3,5.  In that case you will get files;
            sid-1, sid-3 and
            sid-5. Note the lack of an .evt
            file type/extension.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| offlinereglom | Up | reglom |
