|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="tcl3_ringstatus"></a>RingStatus

<a name="AEN102778"></a>## Name

RingStatus -- Widget that shows ring status.

<a name="AEN102781"></a>## Synopsis

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

<a name="AEN102799"></a>## DESCRIPTION

Provides a Tcl megawidget that displays the status of a ringbuffer.
            The widget shows the name, size and total free space of the ring
            A table also shows the PIDs of each consumer along with the number of
            bytes of backlog data for that consumer.

<a name="AEN102802"></a>## OPTIONS



`-name` *name-string*Configures the name of the ring. This is displayed in the widget.

<a name="AEN102811"></a>## METHODS



`update` *ring-info-list*Accepts a list of data compatible with the output
                            of the
                            [[r94870]]
                            command.  This data is used to update the ring size, free space and
                            consumer information table.

<a name="AEN102822"></a>## SEE ALSO

[[r94870]]

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| FrameSequencer | Up | ScaleControl |
