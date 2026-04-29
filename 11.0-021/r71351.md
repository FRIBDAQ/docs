|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="tcl3_ringstatus"></a>RingStatus

<a name="AEN71363"></a>## Name

RingStatus -- Widget that shows ring status.

<a name="AEN71366"></a>## Synopsis

**package require RingStatus
package require ring
            **

**RingStatus *path ?options?*
**

** *path* configure *options...*
**

** *path* cget *option*
**

** *path* update [ringbuffer usage *ringname*]
            **

<a name="AEN71384"></a>## DESCRIPTION

Provides a Tcl megawidget that displays the status of a ringbuffer.
            The widget shows the name, size and total free space of the ring
            A table also shows the PIDs of each consumer along with the number of
            bytes of backlog data for that consumer.

<a name="AEN71387"></a>## OPTIONS



`-name` *name-string*Configures the name of the ring. This is displayed in the widget.

<a name="AEN71396"></a>## METHODS



`update` *ring-info-list*Accepts a list of data compatible with the output
                            of the
                            [[r68240]]
                            command.  This data is used to update the ring size, free space and
                            consumer information table.

<a name="AEN71407"></a>## SEE ALSO

[[r68240]]

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| marker | Up | 3sbsReadout |
