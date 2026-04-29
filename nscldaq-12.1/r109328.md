|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="tcl3_ringstatus"></a>RingStatus

<a name="AEN109342"></a>## Name

RingStatus -- Widget that shows ring status.

<a name="AEN109345"></a>## Synopsis

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

<a name="AEN109363"></a>## DESCRIPTION

Provides a Tcl megawidget that displays the status of a ringbuffer.
            The widget shows the name, size and total free space of the ring
            A table also shows the PIDs of each consumer along with the number of
            bytes of backlog data for that consumer.

<a name="AEN109366"></a>## OPTIONS



`-name` *name-string*Configures the name of the ring. This is displayed in the widget.

<a name="AEN109375"></a>## METHODS



`update` *ring-info-list*Accepts a list of data compatible with the output
                            of the
                            [[r101364]]
                            command.  This data is used to update the ring size, free space and
                            consumer information table.

<a name="AEN109386"></a>## SEE ALSO

[[r101364]]

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| FrameSequencer | Up | ScaleControl |
