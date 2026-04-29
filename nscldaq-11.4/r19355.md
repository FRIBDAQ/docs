|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

<a name="man-3daq"></a># VIII. 3daq

**Table of Contents**[[r19357]] -- RingMaster access.[[r19599]] -- Remote Ring Access[[r19795]] -- Provide zero copy access to low level ring buffers.[[r19854]] -- Low level ring buffer primitives[[r20674]] -- Encapsulates an item in a ring buffer.[[r21164]] -- Encapsulate ring buffer scaler items.[[r21610]] -- Encapsulate a ring buffer state change item.[[r22015]] -- Encapsulate ring items that are lists of text strings.[[r22341]] -- Response to trigger.[[r22537]] -- Provides statistics regarding the number of events produced.[[r22864]] -- Encapsulate a EVB_FRAGMENT ring item
         [[r23179]] -- Event fragment likley not containing a ring item[[r23277]] -- Describe the format of a stream of ringitems.[[r23530]] -- Reports event building parameters.[[r23798]] -- Abnormal end of run.[[r24012]] -- Base class for predicates that select items from
            ring buffers.[[r24354]] -- Select all ring items except some.[[r24540]] -- Only accept specified ring item types.[[r24715]] -- Format of ring items.[[r25214]] -- Functions to create ring items.[[r26134]] -- Abstract base class of data source for ring items.[[r26186]] -- Ringbuffer data source for ring items.[[r26265]] -- Ring item data source from a file[[r26332]] -- Create data sources given a URI[[r26399]] -- Upcast ring items to specific ring item objects.[[r26502]] -- Abstract base class for data sinks.[[r26593]] -- Data sink to a disk file.[[r26735]] -- Data sink that writes to a `CRingBuffer`
[[r26836]] -- Create an appropriate CDataSink object[[r26902]] -- Provides zero copy, low level consumer access to ring buffers[[r27159]] -- Framework event builder client application.[[r27313]] -- Event builder client framework.[[r27379]] -- Client of the event orderer[[r27600]] -- Iterator for event built data.[[r27811]] -- Provide a C++ interface to the server port manager daemon.[[r27968]] -- Report errors conditions in port manager transactions[[r28124]] -- Support the Hytec NADC 2530 Peak sensing ADC.[[r28596]] -- Support for the CAEN 32 bit digitizers[[r29401]] -- CES CBD 8210 CAMAC branch highway driver (obsolete)[[r29779]] -- Support for the CAEN V1190 and V1290
                    multihit, complicated TDC.[[r32171]] -- Support the CCAENV560 non-latching scaler.[[r32345]] -- Support driver for the CAEN V820/V830 latching scaler module.[[r32912]] -- Software support for the CAEN V977 I/O register.[[r33321]] -- Support software for the LeCroy LRS 2551 12 channel CAMAC scaler[[r33441]] -- High level support software for the 32 channel LeCroy LRS 4434 CAMAC scaler module[[r33563]] -- Provide computer busy status support for the BiRA CAMAC
                NIM out module.
            [[r33681]] -- Trigger module for the CES CBD 8210 VME CAMAC Parallel Branch Highway Driver
            [[r33745]] -- Manages CAMAC memory maps.[[r33837]] -- Provide support for a generic CAMAC module.[[r34221]] -- Provides low level support for the BiRa CAMAC Nim output module.[[r34320]] -- Encapsulation of a BiRa 1302 CAMAC controller via CES CBS8210.[[r34670]] -- Support for the SIS 3600 VME latch module.[[r35139]] -- Low level support for SIS 3820 32 channel latching scaler module[[r35855]] -- Abstract base class for reading scalers into a vector[[r35972]] -- Abstract base class for status modules.[[r36047]] -- Abstract base class for triggers[[r36085]] -- Pointer like object for accessing the VME[[r36439]] -- High level support for the LeCroy LRS 1151 VME scaler.[[r36536]] -- Implement a status module using the CAEN V262 module.[[r36630]] -- VME trigger class based on the CAEN V262 I/O module.[[r36691]] -- [[r37044]] -- Support for the CAEN V262 I/O register module.[[r37201]] -- Exception that can be thrown in the event of memory mapping errors.[[r37246]] -- Low level support for the BiRa VME nim output module[[r37530]] -- Convenience base class for implementing VME module support[[r37838]] -- Low Level support for the SIS 3300 Flash ADC module[[r38581]] -- Base class for primitive filters[[r38765]] -- A composite filter composed of primitive filters[[r38985]] -- Integer byte order conversions[[r39181]] -- Abstract base class for thread objects.[[r39324]] -- Thread with synchronized initialization[[r39419]] -- Wait queue for threads[[r39527]] -- Provide Critical Regions, Monitors[[r39704]] -- C++ encapsulation of pthread mutexes.[[r39935]] -- Simple, safe critical section[[r39968]] -- Encapsulate POSIX condition variables.[[r40279]] -- Provide entry/exit guards for object critical regions.[[r40345]] -- Templated class for safe inter-thread messaging.[[r40542]] -- Abstract base authenticator class.[[r40656]] -- Authenticate against a stored password.[[r40854]] -- Authenticate against a unix user name and password.[[r41075]] -- Authenticate against a Tcl List.[[r41183]] -- Authenticate against a list of allowed credentials.[[r41335]] -- Authenticate from a list of TCP/IP hosts[[r41525]] -- Base class for security interactions.[[r41704]] -- Provide an interactor that processes strings.[[r41875]] -- Interact with  file descriptor[[r42011]] -- Separate prompt and input interactors.[[r42146]] -- Parse Uniform Resource Identifiers (URI)[[r42304]] -- Generate license/author credits.[[r42410]] -- Binary I/O operations.[[r42534]] -- Operating system interfaces.[[r42719]] -- class description[[r43088]] -- Simple binary buffered output class with flush.[[r43184]] -- ABC for reading blocks of ring items from a source.[[r43283]] -- CRingBlockreader that reads from file.[[r43320]] -- Encapsulation of a socket file descriptor.[[r44174]] -- class description[[r44293]] -- Exception thrown for TCP/IP connection failures.[[r44415]] -- Exception thrown when connection to peer is lost[[r44525]] -- CTCPNoSuchHost[[r44660]] -- Exception thrown if a nonexistent service is referenced[[r44748]] -- 
            Base class for TCL/Tk applications.
        [[r44801]] -- 
            Class for reporting exceptional conditions in Tcl applications
            via the C++ try/catch mechanism.
        [[r44954]] -- 
            Encapsulate a Tcl interpreter.
        [[r45182]] -- 
            Base class for objects that are associated with a Tcl Interpreter.
        [[r45271]] -- 
            Provide access to Tcl List parsing.
        [[r45390]] -- 
            Encapsulate Tcl Dual ported objects.
        [[r45631]] -- 
            Abstract base class to encapsulate the Tcl object command interface exposed by
            `Tcl_CreateObjCommand`.
        [[r45734]] -- 
            Encapsulate Tcl interpreter variables.
        [[r45939]] -- 
            Provide `argc`, `argv`
            extension commands to Tcl.
        [[r46138]] -- 
            Provide a C++ abstraction wrapper for Tcl Channels.
        [[r46318]] -- 
            Group several related Tcl command extensions and common services they
            may require together.
        [[r46433]] -- 
            Adaptor between `CTCLOjbectProcessor`
            and `CTCLProcessor`.
        [[r46510]] -- 
            Base class for building object oriented Tcl File event handlers.
        [[r46606]] -- 
            Object oriented interface to Tcl's hash table functions.
        [[r46747]] -- 
            Encapsulation of an entry in a Tcl Hash table as encapsulated
            in `CTCLHashTable`
[[r46825]] -- 
            Iterator for visiting all elements of a `CTCLHashTable`
[[r46931]] -- 
            Allows the establishment of an executable object that
            can be scheduled to be invoked when the Tcl/Tk intperpreter
            has no events that require processing.
        [[r47002]] -- 
            Base class for a command that lives in a `CTCLCommandPackage`
[[r47073]] -- 
            Provide an object oriented interace to the Tcl interpreter result.
        [[r47194]] -- 
            Provide a wrapper for the Tcl_DString data type
            and its API
        [[r47421]] -- 
            Abstract base class for C++ objects attached to timer events.
        [[r47501]] -- Run Tcl with event loop.[[r47615]] -- Accept commands on a Tcl channel from the event loop.[[r47837]] -- Event driven command input on stdin/stdout[[r47911]] -- Listener for a Tcl server.[[r48049]] -- Channel commander that is a server instance for `CTCLServer`[[r48132]] -- Provide common functionality for a set of
                related commands.[[r48204]] -- Base class for commands living in a
                    `CTCLObjectPackage`
[[r48314]] -- Hold a configuration[[r49047]] -- Base class for objects tht have a configuration.[[r49277]] -- Abstract base class for the exception class hierarchy.[[r49374]] -- Exceptions that wrap the Unix `errno`[[r49461]] -- Reports and exception for a value out of allowed range.[[r49609]] -- Exception for invalid state transitions.[[r49718]] -- I/O error on a C++ stream.[[r49891]] -- Report errors in universal resource identifiers (uri)s.[[r50086]] -- Exceptions for synchronization class abuse.[[r50231]] -- Report invalid function arguments.[[r50375]] -- Abtract base class for a CSP process[[r50417]] -- Abstract base class for a CSP processing element[[r50478]] -- Base class for a worker that receives fanned out data.[[r50555]] -- Abstract base class for data transport objects.[[r50629]] -- Encapsulate a transport to send data.[[r50705]] -- Encapsulates a transport to receive data[[r50766]] -- Null transport for testing[[r50781]] -- Transport class for test purposes.[[r50860]] -- Registry of clients.[[r50935]] -- Transport to fanout data to several workers.[[r50948]] -- Client for a fanout transport[[r50962]] -- Base class for ring item transports.[[r50974]] -- Transport for ring items to or from ring buffers.[[r51047]] -- Transport ring items to and from files.[[r51125]] -- Create and appropriate ring item transport[[r51146]] -- Base class for ZeroMQ transports[[r51262]] -- ZeroMQ transport that does a connect.[[r51278]] -- ZeroMQ transport that does a listen.[[r51294]] -- ZeroMQ transport that's a ROUTER fanout.[[r51366]] -- Peer, receiver for CZMQRouterTransport(3daq)[[r51448]] -- Forward data to some sink.[[r51461]] -- Fan out a data source without transformations[[r51478]] -- Fanout ring items from some data source.[[r51526]] -- Strategy pattern for classifying ring items[[r51573]] -- Re-sort a stream of ring items by timestamp[[r51594]] -- Run a processing element ina thread.[[r51614]] -- ZeroMQ Threaded worker for ZeroMQ[[r51633]] -- Provide a thread that routes ring items from a source[[r51647]] -- Create transports for an underlying communication scheme.[[r51754]] -- Communicator factory for ZeroMQ[[r51830]] -- Create communication factories.[[r51854]] -- Base class for transports using MPI for communication.[[r52004]] -- Fanout data over MPI to multiple workers.[[r52095]] -- Worker side of a fanout transport (client).[[r52189]] -- Fanout clumps of ring items.[[r52209]] -- Template factory class.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| vmusbcaenupgrader | Up | CRingMaster |
