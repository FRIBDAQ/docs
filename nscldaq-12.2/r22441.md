|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="daq1.ringfragsource"></a>ringFragmentSource

<a name="AEN22445"></a>## Name

ringFragmentSource -- Provide Fragments To EventBuilder From Ring Buffers.

<a name="AEN22448"></a>## Synopsis

**$DAQBIN/ringFragmentSource `options...`
**

<a name="AEN22452"></a>## DESCRIPTION

Provides fragments from a ring buffer to the orderer stage of an
            event builder pipeline.

The program accepts the following options.



`--evbhost`=*hostname*Name of the host in which the event builder pipeline (orderer)
                    is running.

`--evbport`=*portno | 'managed'*Provides the port on which the event builder is listening
                    for data source connections.  If the string managed
                    is used, the event builder is advertising its services via
                    the port manager.  Otherwise this must be the number of a port.
                    The default is managed.

--evbname=*name*This is the name field of the service the event builder
                        is advertising.  The service name is a triplet of the form
                        Orderer:*name*:*uniquifier*
                        The uniquifier is intended to support running several event
                        builders in the same system.  The middle member of the
                        triplet is what should be supplied as the `name`
                        value for this option.

`--info`="InfoString"Provides an info string that describes what these data will
                    be (documentation purposes onyl).  Since this is used by
                    Tcl/Tk substitution characters should be avoided.

`--default-id`=*INT*Obsolete.  Only needed with DAQ 10.x  Provides a source id
                    to use in the event a source id for a fragment annot be determined.
                    NSCLDAQ 11 and 12 use body headers to assure this information
                    is always present.  See `--expectbodyheaders`.

`--ring`=*URI*Provides the URI of the ring from which this program will
                    get data.  This must be a tcp protocol URI.

`--timestampextractor`Only needed for NSCLDAQ-10.x.   Provides a shared object library
                    name containing a timestamp extraction library.

`--expectbodyheaders`If present, the data contain body headers that provide the
                    source id and timestamp for each fragment.  If provided
                    (default is off), there is no need to provide
                    `--timestampextractor` or
                    `--default-id`

`--oneshot`=*1 | 0*Supplies a flag that, if true, tells the program to exit
                    after a run has been processed.  The software counts
                    BEGIN_RUN ring items and when a matching number of
                    END_RUN ring items are seen the program
                    exits if it's in `--oneshot` mode.

`--timeout`In oneshot mode, the maximum number of seconds the source
                    will wait for end runs once the first one has been
                    seen.

`--offset`=*ticks*Provides the ability to compensate for fixed synchronization
                    offsets in data sources.  The signed integer value of this
                    option is added to the timestamps for all fragments.
                    Note that this is added to the fragment header used to prepend
                    all data items.  No modifications to the body occur.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| evbtagger | Up | unglom |
