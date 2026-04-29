|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="daq3-evbclientfw-usercode"></a>CEvbClientApp

<a name="AEN40291"></a>## Name

CEvbClientApp -- Framework event builder client application.

<a name="AEN40294"></a>## Synopsis

```
CEVBClientApp
```

<a name="AEN40324"></a>## DESCRIPTION

`CEvbClientApp` is an abstract base class for
            applications that use the Event builder data source application
            framework.  This class conatains an interface definition
            that consists of some methods that are pure virtual
            and others for which there is a default implementation.

See METHODS below for a description of the base class methods
            as well as the interface methods.
            [[r40431]]
            for more information about the methods that are available for your
            custom code to interface with the remainder of the framework.

<a name="AEN40330"></a>## METHODS



`  CEVBClientApp();`The base class constructor is responsible
                        for registering objects that are constructed with the
                        framework.  Note that all objects of this type that are
                        created will be registered allowing for
                        *super sources* to be created.

` virtual void initialize();`This method is invoked by the framework exactly once.
                        Almost all of your one-time intialization should be
                        performed here.  The base class provides an empty
                        default implementation so that you do not need to override
                        this method if you do not require any one-time initialization.

` virtual  = 0 bool dataReady(int ms);`Called to determine if the data source you are managing
                        has data to process.  `ms` is an
                        estimate of the maximum amount of time you should block
                        prior to returning.

Return true if there is data to
                        be read (in which case `getEvents`
                        will soon be called),  otherwise return false.

` virtual  = 0 void getEvents();`Called to read events from the data source and
                        submit them to the evenbuilder via one or more calls
                        to `CEVBClientFramework::submitFragmentList`.

` virtual void shutdown();`Called when the client is being properly shutdown.
                        You should release any resources that were dynamically
                        allocated by your event source.  This is
                        especially important for resources that involve
                        inter-process communications so that they don' have
                        to close down via a timeout.

<a name="AEN40386"></a>## PUBLIC VARIABLES, TYPES and CONSTANTS

Two types are often used by event fragment sources:
            ClientEventFragment represents the
            metadata for an event fragment along with a pointer to the
            fragment itself.
            `CEVBEventList` is a list of
            ClietEventFragment objects.  It is actually a specific
            std::list and has all of the methods of that class.

The ClientEventFragment type is a struct with the
            following members:



` uint64_t s_timestamp;`The event fragment timestamp.  For event ordering/building
                        to work, the timestamp for all sources must come from a
                        common timebase and be synchronized.

` uint32_t s_sourceId;`Identifies the source.  In the output of both the
                            event orderer and the builder, each fragment will
                            be tagged with its source id.  Source Ids:



- Should be unique from source to source.
- Should produce fragments that are
                                          time ordered.
- Each have their own fragment queue. You
                                          therefore do not need to order fragments
                                          across event source only within sources.


` uint32_t s_size;`The number of bytes in the fragment data.

` void* s_payload;`A pointer to the event fragment.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| fragment.h | Up | CEVBClientFramework |
