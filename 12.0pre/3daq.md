|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

<a name="man-3daq"></a># VIII. 3daq

**Table of Contents**[[r23413]] -- RingMaster access.[[r23655]] -- Remote Ring Access[[r23851]] -- Provide zero copy access to low level ring buffers.[[r23910]] -- Low level ring buffer primitives[[r24730]] -- Encapsulates an item in a ring buffer.[[r25220]] -- Encapsulate ring buffer scaler items.[[r25717]] -- Encapsulate a ring buffer state change item.[[r26159]] -- Encapsulate ring items that are lists of text strings.[[r26521]] -- Response to trigger.[[r26717]] -- Provides statistics regarding the number of events produced.[[r27079]] -- Encapsulate a EVB_FRAGMENT ring item
         [[r27394]] -- Event fragment likley not containing a ring item[[r27492]] -- Describe the format of a stream of ringitems.[[r27746]] -- Reports event building parameters.[[r28014]] -- Abnormal end of run.[[r28228]] -- Base class for predicates that select items from
            ring buffers.[[r28570]] -- Select all ring items except some.[[r28756]] -- Only accept specified ring item types.[[r28931]] -- Format of ring items.[[r29457]] -- Functions to create ring items.[[r30863]] -- Abstract base class of data source for ring items.[[r30915]] -- Ringbuffer data source for ring items.[[r30994]] -- Ring item data source from a file[[r31061]] -- Create data sources given a URI[[r31128]] -- Upcast ring items to specific ring item objects.[[r31231]] -- Abstract base class for data sinks.[[r31322]] -- Data sink to a disk file.[[r31464]] -- Data sink that writes to a `CRingBuffer`
[[r31565]] -- Create an appropriate CDataSink object[[r31631]] -- Provides zero copy, low level consumer access to ring buffers[[r31888]] -- Wrappers for userspace USB library.[[r31931]] -- Report errors from libUSB1[[r31958]] -- Encapsulate low level USB context[[r32008]] -- Provide information about a USB device.[[r32154]] -- I/O object for a USB device[[r32405]] -- Utility methods for JTEC/Wiener XXUSB controllers[[r32721]] -- Top Level Logbook C++ API[[r33477]] -- Encapsulate a person registered in a logbook.[[r33615]] -- Encapsulates shifts in logbook databases[[r33788]] -- Encapsulates runs from logbooks.[[r34279]] -- Encapsulate logbook notes.[[r34607]] -- Define event builder fragment structures.[[r34834]] -- Framework event builder client application.[[r34988]] -- Event builder client framework.[[r35054]] -- Client of the event orderer[[r35275]] -- Iterator for event built data.[[r35486]] -- Provide a C++ interface to the server port manager daemon.[[r35643]] -- Report errors conditions in port manager transactions[[r35799]] -- Support the Hytec NADC 2530 Peak sensing ADC.[[r36271]] -- Support for the CAEN 32 bit digitizers[[r37076]] -- CES CBD 8210 CAMAC branch highway driver (obsolete)[[r37454]] -- Support for the CAEN V1190 and V1290
                    multihit, complicated TDC.[[r39846]] -- Support the CCAENV560 non-latching scaler.[[r40020]] -- Support driver for the CAEN V820/V830 latching scaler module.[[r40587]] -- Software support for the CAEN V977 I/O register.[[r40996]] -- Support software for the LeCroy LRS 2551 12 channel CAMAC scaler[[r41116]] -- High level support software for the 32 channel LeCroy LRS 4434 CAMAC scaler module[[r41238]] -- Provide computer busy status support for the BiRA CAMAC
                NIM out module.
            [[r41356]] -- Trigger module for the CES CBD 8210 VME CAMAC Parallel Branch Highway Driver
            [[r41420]] -- Manages CAMAC memory maps.[[r41512]] -- Provide support for a generic CAMAC module.[[r41896]] -- Provides low level support for the BiRa CAMAC Nim output module.[[r41995]] -- Encapsulation of a BiRa 1302 CAMAC controller via CES CBS8210.[[r42345]] -- Support for the SIS 3600 VME latch module.[[r42814]] -- Low level support for SIS 3820 32 channel latching scaler module[[r43530]] -- Abstract base class for reading scalers into a vector[[r43647]] -- Abstract base class for status modules.[[r43722]] -- Abstract base class for triggers[[r43760]] -- Pointer like object for accessing the VME[[r44114]] -- High level support for the LeCroy LRS 1151 VME scaler.[[r44211]] -- Implement a status module using the CAEN V262 module.[[r44305]] -- VME trigger class based on the CAEN V262 I/O module.[[r44366]] -- [[r44719]] -- Support for the CAEN V262 I/O register module.[[r44876]] -- Exception that can be thrown in the event of memory mapping errors.[[r44921]] -- Low level support for the BiRa VME nim output module[[r45205]] -- Convenience base class for implementing VME module support[[r45513]] -- Low Level support for the SIS 3300 Flash ADC module[[r46256]] -- Base class for primitive filters[[r46440]] -- A composite filter composed of primitive filters[[r46660]] -- Ring item filter application class.[[r46733]] -- Integer byte order conversions[[r46929]] -- Abstract base class for thread objects.[[r47072]] -- Thread with synchronized initialization[[r47167]] -- Wait queue for threads[[r47275]] -- Provide Critical Regions, Monitors[[r47452]] -- C++ encapsulation of pthread mutexes.[[r47683]] -- Simple, safe critical section[[r47716]] -- Encapsulate POSIX condition variables.[[r48027]] -- Provide entry/exit guards for object critical regions.[[r48093]] -- Templated class for safe inter-thread messaging.[[r48290]] -- Abstract base authenticator class.[[r48404]] -- Authenticate against a stored password.[[r48602]] -- Authenticate against a unix user name and password.[[r48823]] -- Authenticate against a Tcl List.[[r48931]] -- Authenticate against a list of allowed credentials.[[r49083]] -- Authenticate from a list of TCP/IP hosts[[r49273]] -- Base class for security interactions.[[r49452]] -- Provide an interactor that processes strings.[[r49623]] -- Interact with  file descriptor[[r49759]] -- Separate prompt and input interactors.[[r49894]] -- Parse Uniform Resource Identifiers (URI)[[r50052]] -- Generate license/author credits.[[r50158]] -- Binary I/O operations.[[r50282]] -- Operating system interfaces.[[r50467]] -- class description[[r50836]] -- Simple binary buffered output class with flush.[[r50932]] -- ABC for reading blocks of ring items from a source.[[r51031]] -- CRingBlockreader that reads from file.[[r51068]] -- Subsecond measurement of elapsed times.[[r51084]] -- Encapsulation of a socket file descriptor.[[r51938]] -- class description[[r52057]] -- Exception thrown for TCP/IP connection failures.[[r52179]] -- Exception thrown when connection to peer is lost[[r52289]] -- CTCPNoSuchHost[[r52424]] -- Exception thrown if a nonexistent service is referenced[[r52512]] -- 
            Base class for TCL/Tk applications.
        [[r52565]] -- 
            Class for reporting exceptional conditions in Tcl applications
            via the C++ try/catch mechanism.
        [[r52718]] -- 
            Encapsulate a Tcl interpreter.
        [[r52946]] -- 
            Base class for objects that are associated with a Tcl Interpreter.
        [[r53035]] -- 
            Provide access to Tcl List parsing.
        [[r53154]] -- 
            Encapsulate Tcl Dual ported objects.
        [[r53395]] -- 
            Abstract base class to encapsulate the Tcl object command interface exposed by
            `Tcl_CreateObjCommand`.
        [[r53498]] -- 
            Encapsulate Tcl interpreter variables.
        [[r53703]] -- 
            Provide `argc`, `argv`
            extension commands to Tcl.
        [[r53902]] -- 
            Provide a C++ abstraction wrapper for Tcl Channels.
        [[r54082]] -- 
            Group several related Tcl command extensions and common services they
            may require together.
        [[r54197]] -- 
            Adaptor between `CTCLOjbectProcessor`
            and `CTCLProcessor`.
        [[r54274]] -- 
            Base class for building object oriented Tcl File event handlers.
        [[r54370]] -- 
            Object oriented interface to Tcl's hash table functions.
        [[r54511]] -- 
            Encapsulation of an entry in a Tcl Hash table as encapsulated
            in `CTCLHashTable`
[[r54589]] -- 
            Iterator for visiting all elements of a `CTCLHashTable`
[[r54695]] -- 
            Allows the establishment of an executable object that
            can be scheduled to be invoked when the Tcl/Tk intperpreter
            has no events that require processing.
        [[r54766]] -- 
            Base class for a command that lives in a `CTCLCommandPackage`
[[r54837]] -- 
            Provide an object oriented interace to the Tcl interpreter result.
        [[r54958]] -- 
            Provide a wrapper for the Tcl_DString data type
            and its API
        [[r55185]] -- 
            Abstract base class for C++ objects attached to timer events.
        [[r55265]] -- Run Tcl with event loop.[[r55379]] -- Accept commands on a Tcl channel from the event loop.[[r55601]] -- Event driven command input on stdin/stdout[[r55675]] -- Listener for a Tcl server.[[r55813]] -- Channel commander that is a server instance for `CTCLServer`[[r55896]] -- Provide common functionality for a set of
                related commands.[[r55968]] -- Base class for commands living in a
                    `CTCLObjectPackage`
[[r56078]] -- Hold a configuration[[r56811]] -- Base class for objects tht have a configuration.[[r57041]] -- Abstract base class for the exception class hierarchy.[[r57138]] -- Exceptions that wrap the Unix `errno`[[r57225]] -- Reports and exception for a value out of allowed range.[[r57373]] -- Exception for invalid state transitions.[[r57482]] -- I/O error on a C++ stream.[[r57655]] -- Report errors in universal resource identifiers (uri)s.[[r57850]] -- Exceptions for synchronization class abuse.[[r57995]] -- Report invalid function arguments.[[r58139]] -- Suport dynamic configuration of Pixie16 modules via DDASReadout Server.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| vmusbcaenupgrader | Up | CRingMaster |
