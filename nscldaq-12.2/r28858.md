|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

<a name="man-3daq"></a># VIII. 3daq

**Table of Contents**[[r28860]] -- RingMaster access.[[r29102]] -- Remote Ring Access[[r29295]] -- Provide zero copy access to low level ring buffers.[[r29354]] -- Low level ring buffer primitives[[r30177]] -- Encapsulates an item in a ring buffer.[[r30665]] -- Encapsulate ring buffer scaler items.[[r31162]] -- Encapsulate a ring buffer state change item.[[r31604]] -- Encapsulate ring items that are lists of text strings.[[r31966]] -- Response to trigger.[[r32162]] -- Provides statistics regarding the number of events produced.[[r32524]] -- Encapsulate a EVB_FRAGMENT ring item
         [[r32839]] -- Event fragment likley not containing a ring item[[r32937]] -- Describe the format of a stream of ringitems.[[r33191]] -- Reports event building parameters.[[r33459]] -- Abnormal end of run.[[r33673]] -- Base class for predicates that select items from
            ring buffers.[[r34015]] -- Select all ring items except some.[[r34201]] -- Only accept specified ring item types.[[r34376]] -- Format of ring items.[[r34902]] -- Functions to create ring items.[[r36308]] -- Abstract base class of data source for ring items.[[r36360]] -- Ringbuffer data source for ring items.[[r36439]] -- Ring item data source from a file[[r36506]] -- Create data sources given a URI[[r36573]] -- Upcast ring items to specific ring item objects.[[r36676]] -- Abstract base class for data sinks.[[r36767]] -- Data sink to a disk file.[[r36909]] -- Data sink that writes to a `CRingBuffer`
[[r37010]] -- Create an appropriate CDataSink object[[r37076]] -- Provides zero copy, low level consumer access to ring buffers[[r37333]] -- Wrappers for userspace USB library.[[r37376]] -- Report errors from libUSB1[[r37403]] -- Encapsulate low level USB context[[r37453]] -- Provide information about a USB device.[[r37599]] -- I/O object for a USB device[[r37850]] -- Utility methods for JTEC/Wiener XXUSB controllers[[r38166]] -- Top Level Logbook C++ API[[r38922]] -- Encapsulate a person registered in a logbook.[[r39058]] -- Encapsulates shifts in logbook databases[[r39231]] -- Encapsulates runs from logbooks.[[r39722]] -- Encapsulate logbook notes.[[r40050]] -- Define event builder fragment structures.[[r40277]] -- Framework event builder client application.[[r40431]] -- Event builder client framework.[[r40497]] -- Client of the event orderer[[r40718]] -- Iterator for event built data.[[r40929]] -- Provide a C++ interface to the server port manager daemon.[[r41090]] -- Report errors conditions in port manager transactions[[r41251]] -- Support the Hytec NADC 2530 Peak sensing ADC.[[r41723]] -- Support for the CAEN 32 bit digitizers[[r42528]] -- CES CBD 8210 CAMAC branch highway driver (obsolete)[[r42906]] -- Support for the CAEN V1190 and V1290
                    multihit, complicated TDC.[[r45298]] -- Support the CCAENV560 non-latching scaler.[[r45472]] -- Support driver for the CAEN V820/V830 latching scaler module.[[r46039]] -- Software support for the CAEN V977 I/O register.[[r46448]] -- Support software for the LeCroy LRS 2551 12 channel CAMAC scaler[[r46568]] -- High level support software for the 32 channel LeCroy LRS 4434 CAMAC scaler module[[r46690]] -- Provide computer busy status support for the BiRA CAMAC
                NIM out module.
            [[r46808]] -- Trigger module for the CES CBD 8210 VME CAMAC Parallel Branch Highway Driver
            [[r46872]] -- Manages CAMAC memory maps.[[r46964]] -- Provide support for a generic CAMAC module.[[r47348]] -- Provides low level support for the BiRa CAMAC Nim output module.[[r47447]] -- Encapsulation of a BiRa 1302 CAMAC controller via CES CBS8210.[[r47797]] -- Support for the SIS 3600 VME latch module.[[r48266]] -- Low level support for SIS 3820 32 channel latching scaler module[[r48982]] -- Abstract base class for reading scalers into a vector[[r49099]] -- Abstract base class for status modules.[[r49174]] -- Abstract base class for triggers[[r49212]] -- Pointer like object for accessing the VME[[r49566]] -- High level support for the LeCroy LRS 1151 VME scaler.[[r49663]] -- Implement a status module using the CAEN V262 module.[[r49757]] -- VME trigger class based on the CAEN V262 I/O module.[[r49818]] -- [[r50171]] -- Support for the CAEN V262 I/O register module.[[r50328]] -- Exception that can be thrown in the event of memory mapping errors.[[r50373]] -- Low level support for the BiRa VME nim output module[[r50657]] -- Convenience base class for implementing VME module support[[r50965]] -- Low Level support for the SIS 3300 Flash ADC module[[r51708]] -- Base class for primitive filters[[r51892]] -- A composite filter composed of primitive filters[[r52112]] -- Ring item filter application class.[[r52185]] -- Integer byte order conversions[[r52381]] -- Abstract base class for thread objects.[[r52524]] -- Thread with synchronized initialization[[r52619]] -- Wait queue for threads[[r52727]] -- Provide Critical Regions, Monitors[[r52904]] -- C++ encapsulation of pthread mutexes.[[r53135]] -- Simple, safe critical section[[r53168]] -- Encapsulate POSIX condition variables.[[r53479]] -- Provide entry/exit guards for object critical regions.[[r53545]] -- Templated class for safe inter-thread messaging.[[r53742]] -- Abstract base authenticator class.[[r53854]] -- Authenticate against a stored password.[[r54052]] -- Authenticate against a unix user name and password.[[r54273]] -- Authenticate against a Tcl List.[[r54377]] -- Authenticate against a list of allowed credentials.[[r54529]] -- Authenticate from a list of TCP/IP hosts[[r54719]] -- Base class for security interactions.[[r54898]] -- Provide an interactor that processes strings.[[r55069]] -- Interact with  file descriptor[[r55205]] -- Separate prompt and input interactors.[[r55340]] -- Parse Uniform Resource Identifiers (URI)[[r55490]] -- Generate license/author credits.[[r55596]] -- Binary I/O operations.[[r55720]] -- Operating system interfaces.[[r55905]] -- class description[[r56274]] -- Simple binary buffered output class with flush.[[r56370]] -- ABC for reading blocks of ring items from a source.[[r56469]] -- CRingBlockreader that reads from file.[[r56506]] -- Subsecond measurement of elapsed times.[[r56522]] -- Encapsulation of a socket file descriptor.[[r57376]] -- class description[[r57495]] -- Exception thrown for TCP/IP connection failures.[[r57617]] -- Exception thrown when connection to peer is lost[[r57727]] -- CTCPNoSuchHost[[r57862]] -- Exception thrown if a nonexistent service is referenced[[r57950]] -- 
            Base class for TCL/Tk applications.
        [[r58003]] -- 
            Class for reporting exceptional conditions in Tcl applications
            via the C++ try/catch mechanism.
        [[r58156]] -- 
            Encapsulate a Tcl interpreter.
        [[r58384]] -- 
            Base class for objects that are associated with a Tcl Interpreter.
        [[r58473]] -- 
            Provide access to Tcl List parsing.
        [[r58592]] -- 
            Encapsulate Tcl Dual ported objects.
        [[r58833]] -- 
            Abstract base class to encapsulate the Tcl object command interface exposed by
            `Tcl_CreateObjCommand`.
        [[r58936]] -- 
            Encapsulate Tcl interpreter variables.
        [[r59141]] -- 
            Provide `argc`, `argv`
            extension commands to Tcl.
        [[r59340]] -- 
            Provide a C++ abstraction wrapper for Tcl Channels.
        [[r59520]] -- 
            Group several related Tcl command extensions and common services they
            may require together.
        [[r59635]] -- 
            Adaptor between `CTCLOjbectProcessor`
            and `CTCLProcessor`.
        [[r59712]] -- 
            Base class for building object oriented Tcl File event handlers.
        [[r59808]] -- 
            Object oriented interface to Tcl's hash table functions.
        [[r59949]] -- 
            Encapsulation of an entry in a Tcl Hash table as encapsulated
            in `CTCLHashTable`
[[r60027]] -- 
            Iterator for visiting all elements of a `CTCLHashTable`
[[r60133]] -- 
            Allows the establishment of an executable object that
            can be scheduled to be invoked when the Tcl/Tk intperpreter
            has no events that require processing.
        [[r60204]] -- 
            Base class for a command that lives in a `CTCLCommandPackage`
[[r60275]] -- 
            Provide an object oriented interace to the Tcl interpreter result.
        [[r60396]] -- 
            Provide a wrapper for the Tcl_DString data type
            and its API
        [[r60623]] -- 
            Abstract base class for C++ objects attached to timer events.
        [[r60703]] -- Run Tcl with event loop.[[r60817]] -- Accept commands on a Tcl channel from the event loop.[[r61039]] -- Event driven command input on stdin/stdout[[r61113]] -- Listener for a Tcl server.[[r61251]] -- Channel commander that is a server instance for `CTCLServer`[[r61334]] -- Provide common functionality for a set of
                related commands.[[r61406]] -- Base class for commands living in a
                    `CTCLObjectPackage`
[[r61516]] -- Hold a configuration[[r62249]] -- Base class for objects tht have a configuration.[[r62479]] -- Abstract base class for the exception class hierarchy.[[r62576]] -- Exceptions that wrap the Unix `errno`[[r62663]] -- Reports and exception for a value out of allowed range.[[r62811]] -- Exception for invalid state transitions.[[r62920]] -- I/O error on a C++ stream.[[r63093]] -- Report errors in universal resource identifiers (uri)s.[[r63288]] -- Exceptions for synchronization class abuse.[[r63433]] -- Report invalid function arguments.[[r63577]] -- Support dynamic configuration of Pixie-16 modules via DDASReadout Server.[[r63761]] -- Low Level Access To Digitizers[[r64270]] -- Provide compile time checked API to CAEN Nextgen digitizers DPP-PHA[[r67976]] -- Encapsulate module configuration for CAEN Nextgen digitizers[[r69262]] -- Tcl scripted configuration.[[r69393]] -- Event Segment configured with Tcl[[r69479]] -- Event segment for single VX2750 DPP-PHA module[[r69552]] -- Manage readout triggers.[[r69641]] -- Abtract base class for a CSP process[[r69683]] -- Abstract base class for a CSP processing element[[r69744]] -- Base class for a worker that receives fanned out data.[[r69821]] -- Abstract base class for data transport objects.[[r69895]] -- Encapsulate a transport to send data.[[r69971]] -- Encapsulates a transport to receive data[[r70032]] -- Null transport for testing[[r70047]] -- Transport class for test purposes.[[r70126]] -- Registry of clients.[[r70201]] -- Transport to fanout data to several workers.[[r70214]] -- Client for a fanout transport[[r70228]] -- Base class for ring item transports.[[r70240]] -- Transport for ring items to or from ring buffers.[[r70313]] -- Transport ring items to and from files.[[r70391]] -- Create and appropriate ring item transport[[r70412]] -- Base class for ZeroMQ transports[[r70528]] -- ZeroMQ transport that does a connect.[[r70544]] -- ZeroMQ transport that does a listen.[[r70560]] -- ZeroMQ transport that's a ROUTER fanout.[[r70632]] -- Peer, receiver for CZMQRouterTransport(3daq)[[r70714]] -- Forward data to some sink.[[r70727]] -- Fan out a data source without transformations[[r70744]] -- Fanout ring items from some data source.[[r70792]] -- Strategy pattern for classifying ring items[[r70839]] -- Re-sort a stream of ring items by timestamp[[r70860]] -- Run a processing element ina thread.[[r70880]] -- ZeroMQ Threaded worker for ZeroMQ[[r70899]] -- Provide a thread that routes ring items from a source[[r70913]] -- Create transports for an underlying communication scheme.[[r71020]] -- Communicator factory for ZeroMQ[[r71096]] -- Create communication factories.[[r71120]] -- Base class for transports using MPI for communication.[[r71270]] -- Fanout data over MPI to multiple workers.[[r71361]] -- Worker side of a fanout transport (client).[[r71455]] -- Fanout clumps of ring items.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| vmusbcaenupgrader | Up | CRingMaster |
