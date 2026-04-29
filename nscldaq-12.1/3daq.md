|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

<a name="man-3daq"></a># VIII. 3daq

**Table of Contents**[[r27375]] -- RingMaster access.[[r27617]] -- Remote Ring Access[[r27810]] -- Provide zero copy access to low level ring buffers.[[r27869]] -- Low level ring buffer primitives[[r28692]] -- Encapsulates an item in a ring buffer.[[r29180]] -- Encapsulate ring buffer scaler items.[[r29677]] -- Encapsulate a ring buffer state change item.[[r30119]] -- Encapsulate ring items that are lists of text strings.[[r30481]] -- Response to trigger.[[r30677]] -- Provides statistics regarding the number of events produced.[[r31039]] -- Encapsulate a EVB_FRAGMENT ring item
         [[r31354]] -- Event fragment likley not containing a ring item[[r31452]] -- Describe the format of a stream of ringitems.[[r31706]] -- Reports event building parameters.[[r31974]] -- Abnormal end of run.[[r32188]] -- Base class for predicates that select items from
            ring buffers.[[r32530]] -- Select all ring items except some.[[r32716]] -- Only accept specified ring item types.[[r32891]] -- Format of ring items.[[r33417]] -- Functions to create ring items.[[r34823]] -- Abstract base class of data source for ring items.[[r34875]] -- Ringbuffer data source for ring items.[[r34954]] -- Ring item data source from a file[[r35021]] -- Create data sources given a URI[[r35088]] -- Upcast ring items to specific ring item objects.[[r35191]] -- Abstract base class for data sinks.[[r35282]] -- Data sink to a disk file.[[r35424]] -- Data sink that writes to a `CRingBuffer`
[[r35525]] -- Create an appropriate CDataSink object[[r35591]] -- Provides zero copy, low level consumer access to ring buffers[[r35848]] -- Wrappers for userspace USB library.[[r35891]] -- Report errors from libUSB1[[r35918]] -- Encapsulate low level USB context[[r35968]] -- Provide information about a USB device.[[r36114]] -- I/O object for a USB device[[r36365]] -- Utility methods for JTEC/Wiener XXUSB controllers[[r36681]] -- Top Level Logbook C++ API[[r37437]] -- Encapsulate a person registered in a logbook.[[r37573]] -- Encapsulates shifts in logbook databases[[r37746]] -- Encapsulates runs from logbooks.[[r38237]] -- Encapsulate logbook notes.[[r38565]] -- Define event builder fragment structures.[[r38792]] -- Framework event builder client application.[[r38946]] -- Event builder client framework.[[r39012]] -- Client of the event orderer[[r39233]] -- Iterator for event built data.[[r39444]] -- Provide a C++ interface to the server port manager daemon.[[r39605]] -- Report errors conditions in port manager transactions[[r39766]] -- Support the Hytec NADC 2530 Peak sensing ADC.[[r40238]] -- Support for the CAEN 32 bit digitizers[[r41043]] -- CES CBD 8210 CAMAC branch highway driver (obsolete)[[r41421]] -- Support for the CAEN V1190 and V1290
                    multihit, complicated TDC.[[r43813]] -- Support the CCAENV560 non-latching scaler.[[r43987]] -- Support driver for the CAEN V820/V830 latching scaler module.[[r44554]] -- Software support for the CAEN V977 I/O register.[[r44963]] -- Support software for the LeCroy LRS 2551 12 channel CAMAC scaler[[r45083]] -- High level support software for the 32 channel LeCroy LRS 4434 CAMAC scaler module[[r45205]] -- Provide computer busy status support for the BiRA CAMAC
                NIM out module.
            [[r45323]] -- Trigger module for the CES CBD 8210 VME CAMAC Parallel Branch Highway Driver
            [[r45387]] -- Manages CAMAC memory maps.[[r45479]] -- Provide support for a generic CAMAC module.[[r45863]] -- Provides low level support for the BiRa CAMAC Nim output module.[[r45962]] -- Encapsulation of a BiRa 1302 CAMAC controller via CES CBS8210.[[r46312]] -- Support for the SIS 3600 VME latch module.[[r46781]] -- Low level support for SIS 3820 32 channel latching scaler module[[r47497]] -- Abstract base class for reading scalers into a vector[[r47614]] -- Abstract base class for status modules.[[r47689]] -- Abstract base class for triggers[[r47727]] -- Pointer like object for accessing the VME[[r48081]] -- High level support for the LeCroy LRS 1151 VME scaler.[[r48178]] -- Implement a status module using the CAEN V262 module.[[r48272]] -- VME trigger class based on the CAEN V262 I/O module.[[r48333]] -- [[r48686]] -- Support for the CAEN V262 I/O register module.[[r48843]] -- Exception that can be thrown in the event of memory mapping errors.[[r48888]] -- Low level support for the BiRa VME nim output module[[r49172]] -- Convenience base class for implementing VME module support[[r49480]] -- Low Level support for the SIS 3300 Flash ADC module[[r50223]] -- Base class for primitive filters[[r50407]] -- A composite filter composed of primitive filters[[r50627]] -- Ring item filter application class.[[r50700]] -- Integer byte order conversions[[r50896]] -- Abstract base class for thread objects.[[r51039]] -- Thread with synchronized initialization[[r51134]] -- Wait queue for threads[[r51242]] -- Provide Critical Regions, Monitors[[r51419]] -- C++ encapsulation of pthread mutexes.[[r51650]] -- Simple, safe critical section[[r51683]] -- Encapsulate POSIX condition variables.[[r51994]] -- Provide entry/exit guards for object critical regions.[[r52060]] -- Templated class for safe inter-thread messaging.[[r52257]] -- Abstract base authenticator class.[[r52369]] -- Authenticate against a stored password.[[r52567]] -- Authenticate against a unix user name and password.[[r52788]] -- Authenticate against a Tcl List.[[r52892]] -- Authenticate against a list of allowed credentials.[[r53044]] -- Authenticate from a list of TCP/IP hosts[[r53234]] -- Base class for security interactions.[[r53413]] -- Provide an interactor that processes strings.[[r53584]] -- Interact with  file descriptor[[r53720]] -- Separate prompt and input interactors.[[r53855]] -- Parse Uniform Resource Identifiers (URI)[[r54005]] -- Generate license/author credits.[[r54111]] -- Binary I/O operations.[[r54235]] -- Operating system interfaces.[[r54420]] -- class description[[r54789]] -- Simple binary buffered output class with flush.[[r54885]] -- ABC for reading blocks of ring items from a source.[[r54984]] -- CRingBlockreader that reads from file.[[r55021]] -- Subsecond measurement of elapsed times.[[r55037]] -- Encapsulation of a socket file descriptor.[[r55891]] -- class description[[r56010]] -- Exception thrown for TCP/IP connection failures.[[r56132]] -- Exception thrown when connection to peer is lost[[r56242]] -- CTCPNoSuchHost[[r56377]] -- Exception thrown if a nonexistent service is referenced[[r56465]] -- 
            Base class for TCL/Tk applications.
        [[r56518]] -- 
            Class for reporting exceptional conditions in Tcl applications
            via the C++ try/catch mechanism.
        [[r56671]] -- 
            Encapsulate a Tcl interpreter.
        [[r56899]] -- 
            Base class for objects that are associated with a Tcl Interpreter.
        [[r56988]] -- 
            Provide access to Tcl List parsing.
        [[r57107]] -- 
            Encapsulate Tcl Dual ported objects.
        [[r57348]] -- 
            Abstract base class to encapsulate the Tcl object command interface exposed by
            `Tcl_CreateObjCommand`.
        [[r57451]] -- 
            Encapsulate Tcl interpreter variables.
        [[r57656]] -- 
            Provide `argc`, `argv`
            extension commands to Tcl.
        [[r57855]] -- 
            Provide a C++ abstraction wrapper for Tcl Channels.
        [[r58035]] -- 
            Group several related Tcl command extensions and common services they
            may require together.
        [[r58150]] -- 
            Adaptor between `CTCLOjbectProcessor`
            and `CTCLProcessor`.
        [[r58227]] -- 
            Base class for building object oriented Tcl File event handlers.
        [[r58323]] -- 
            Object oriented interface to Tcl's hash table functions.
        [[r58464]] -- 
            Encapsulation of an entry in a Tcl Hash table as encapsulated
            in `CTCLHashTable`
[[r58542]] -- 
            Iterator for visiting all elements of a `CTCLHashTable`
[[r58648]] -- 
            Allows the establishment of an executable object that
            can be scheduled to be invoked when the Tcl/Tk intperpreter
            has no events that require processing.
        [[r58719]] -- 
            Base class for a command that lives in a `CTCLCommandPackage`
[[r58790]] -- 
            Provide an object oriented interace to the Tcl interpreter result.
        [[r58911]] -- 
            Provide a wrapper for the Tcl_DString data type
            and its API
        [[r59138]] -- 
            Abstract base class for C++ objects attached to timer events.
        [[r59218]] -- Run Tcl with event loop.[[r59332]] -- Accept commands on a Tcl channel from the event loop.[[r59554]] -- Event driven command input on stdin/stdout[[r59628]] -- Listener for a Tcl server.[[r59766]] -- Channel commander that is a server instance for `CTCLServer`[[r59849]] -- Provide common functionality for a set of
                related commands.[[r59921]] -- Base class for commands living in a
                    `CTCLObjectPackage`
[[r60031]] -- Hold a configuration[[r60764]] -- Base class for objects tht have a configuration.[[r60994]] -- Abstract base class for the exception class hierarchy.[[r61091]] -- Exceptions that wrap the Unix `errno`[[r61178]] -- Reports and exception for a value out of allowed range.[[r61326]] -- Exception for invalid state transitions.[[r61435]] -- I/O error on a C++ stream.[[r61608]] -- Report errors in universal resource identifiers (uri)s.[[r61803]] -- Exceptions for synchronization class abuse.[[r61948]] -- Report invalid function arguments.[[r62092]] -- Support dynamic configuration of Pixie-16 modules via DDASReadout Server.[[r62276]] -- Low Level Access To Digitizers[[r62785]] -- Provide compile time checked API to CAEN Nextgen digitizers DPP-PHA[[r66491]] -- Encapsulate module configuration for CAEN Nextgen digitizers[[r67777]] -- Tcl scripted configuration.[[r67908]] -- Event Segment configured with Tcl[[r67994]] -- Event segment for single VX2750 DPP-PHA module[[r68067]] -- Manage readout triggers.[[r68156]] -- Abtract base class for a CSP process[[r68198]] -- Abstract base class for a CSP processing element[[r68259]] -- Base class for a worker that receives fanned out data.[[r68336]] -- Abstract base class for data transport objects.[[r68410]] -- Encapsulate a transport to send data.[[r68486]] -- Encapsulates a transport to receive data[[r68547]] -- Null transport for testing[[r68562]] -- Transport class for test purposes.[[r68641]] -- Registry of clients.[[r68716]] -- Transport to fanout data to several workers.[[r68729]] -- Client for a fanout transport[[r68743]] -- Base class for ring item transports.[[r68755]] -- Transport for ring items to or from ring buffers.[[r68828]] -- Transport ring items to and from files.[[r68906]] -- Create and appropriate ring item transport[[r68927]] -- Base class for ZeroMQ transports[[r69043]] -- ZeroMQ transport that does a connect.[[r69059]] -- ZeroMQ transport that does a listen.[[r69075]] -- ZeroMQ transport that's a ROUTER fanout.[[r69147]] -- Peer, receiver for CZMQRouterTransport(3daq)[[r69229]] -- Forward data to some sink.[[r69242]] -- Fan out a data source without transformations[[r69259]] -- Fanout ring items from some data source.[[r69307]] -- Strategy pattern for classifying ring items[[r69354]] -- Re-sort a stream of ring items by timestamp[[r69375]] -- Run a processing element ina thread.[[r69395]] -- ZeroMQ Threaded worker for ZeroMQ[[r69414]] -- Provide a thread that routes ring items from a source[[r69428]] -- Create transports for an underlying communication scheme.[[r69535]] -- Communicator factory for ZeroMQ[[r69611]] -- Create communication factories.[[r69635]] -- Base class for transports using MPI for communication.[[r69785]] -- Fanout data over MPI to multiple workers.[[r69876]] -- Worker side of a fanout transport (client).[[r69970]] -- Fanout clumps of ring items.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| vmusbcaenupgrader | Up | CRingMaster |
