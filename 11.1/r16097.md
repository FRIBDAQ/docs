|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

<a name="man-3daq"></a># VIII. 3daq

**Table of Contents**[[r16099]] -- RingMaster access.[[r16338]] -- Remote Ring Access[[r16531]] -- Low level ring buffer primitives[[r17341]] -- Encapsulates an item in a ring buffer.[[r17808]] -- Encapsulate ring buffer scaler items.[[r18244]] -- Encapsulate a ring buffer state change item.[[r18639]] -- Encapsulate ring items that are lists of text strings.[[r18955]] -- Response to trigger.[[r19141]] -- Provides statistics regarding the number of events produced.[[r19458]] -- Encapsulate a EVB_FRAGMENT ring item
         [[r19763]] -- Event fragment likley not containing a ring item[[r19851]] -- Describe the format of a stream of ringitems.[[r20094]] -- Reports event building parameters.[[r20352]] -- Abnormal end of run.[[r20564]] -- Base class for predicates that select items from
            ring buffers.[[r20896]] -- Select all ring items except some.[[r21072]] -- Only accept specified ring item types.[[r21237]] -- Format of ring items.[[r21726]] -- Functions to create ring items.[[r22636]] -- Abstract base class of data source for ring items.[[r22678]] -- Ringbuffer data source for ring items.[[r22747]] -- Ring item data source from a file[[r22804]] -- Create data sources given a URI[[r22861]] -- Upcast ring items to specific ring item objects.[[r22954]] -- Abstract base class for data sinks.[[r23043]] -- Data sink to a disk file.[[r23183]] -- Data sink that writes to a `CRingBuffer`
[[r23282]] -- Create an appropriate CDataSink object[[r23346]] -- Framework event builder client application.[[r23490]] -- Event builder client framework.[[r23546]] -- Client of the event orderer[[r23757]] -- Provide a C++ interface to the server port manager daemon.[[r23912]] -- Report errors conditions in port manager transactions[[r24066]] -- Support the Hytec NADC 2530 Peak sensing ADC.[[r24528]] -- Support for the CAEN 32 bit digitizers[[r25331]] -- CES CBD 8210 CAMAC branch highway driver (obsolete)[[r25699]] -- Support for the CAEN V1190 and V1290
                    multihit, complicated TDC.[[r28081]] -- Support the CCAENV560 non-latching scaler.[[r28245]] -- Support driver for the CAEN V820/V830 latching scaler module.[[r28802]] -- Software support for the CAEN V977 I/O register.[[r29201]] -- Support software for the LeCroy LRS 2551 12 channel CAMAC scaler[[r29311]] -- High level support software for the 32 channel LeCroy LRS 4434 CAMAC scaler module[[r29423]] -- Provide computer busy status support for the BiRA CAMAC
                NIM out module.
            [[r29531]] -- Trigger module for the CES CBD 8210 VME CAMAC Parallel Branch Highway Driver
            [[r29585]] -- Manages CAMAC memory maps.[[r29667]] -- Provide support for a generic CAMAC module.[[r30041]] -- Provides low level support for the BiRa CAMAC Nim output module.[[r30130]] -- Encapsulation of a BiRa 1302 CAMAC controller via CES CBS8210.[[r30470]] -- Support for the SIS 3600 VME latch module.[[r30929]] -- Low level support for SIS 3820 32 channel latching scaler module[[r31635]] -- Abstract base class for reading scalers into a vector[[r31742]] -- Abstract base class for status modules.[[r31807]] -- Abstract base class for triggers[[r31835]] -- Pointer like object for accessing the VME[[r32179]] -- High level support for the LeCroy LRS 1151 VME scaler.[[r32266]] -- Implement a status module using the CAEN V262 module.[[r32350]] -- VME trigger class based on the CAEN V262 I/O module.[[r32401]] -- [[r32744]] -- Support for the CAEN V262 I/O register module.[[r32891]] -- Exception that can be thrown in the event of memory mapping errors.[[r32926]] -- Low level support for the BiRa VME nim output module[[r33200]] -- Convenience base class for implementing VME module support[[r33498]] -- Low Level support for the SIS 3300 Flash ADC module[[r34231]] -- Base class for primitive filters[[r34413]] -- A composite filter composed of primitive filters[[r34631]] -- Integer byte order conversions[[r34817]] -- Abstract base class for thread objects.[[r34951]] -- Wait queue for threads[[r35049]] -- Provide Critical Regions, Monitors[[r35216]] -- C++ encapsulation of pthread mutexes.[[r35437]] -- Simple, safe critical section[[r35468]] -- Encapsulate POSIX condition variables.[[r35769]] -- Provide entry/exit guards for object critical regions.[[r35825]] -- Templated class for safe inter-thread messaging.[[r36012]] -- Abstract base authenticator class.[[r36116]] -- Authenticate against a stored password.[[r36304]] -- Authenticate against a unix user name and password.[[r36515]] -- Authenticate against a Tcl List.[[r36613]] -- Authenticate against a list of allowed credentials.[[r36755]] -- Authenticate from a list of TCP/IP hosts[[r36935]] -- Base class for security interactions.[[r37104]] -- Provide an interactor that processes strings.[[r37265]] -- Interact with  file descriptor[[r37391]] -- Separate prompt and input interactors.[[r37516]] -- Parse Uniform Resource Identifiers (URI)[[r37664]] -- Generate license/author credits.[[r37760]] -- class description[[r38119]] -- 
            Base class for TCL/Tk applications.
        [[r38162]] -- 
            Class for reporting exceptional conditions in Tcl applications
            via the C++ try/catch mechanism.
        [[r38305]] -- 
            Encapsulate a Tcl interpreter.
        [[r38560]] -- 
            Base class for objects that are associated with a Tcl Interpreter.
        [[r38639]] -- 
            Provide access to Tcl List parsing.
        [[r38748]] -- 
            Encapsulate Tcl Dual ported objects.
        [[r38979]] -- 
            Abstract base class to encapsulate the Tcl object command interface exposed by
            `Tcl_CreateObjCommand`.
        [[r39150]] -- 
            Encapsulate Tcl interpreter variables.
        [[r39345]] -- 
            Provide `argc`, `argv`
            extension commands to Tcl.
        [[r39534]] -- 
            Provide a C++ abstraction wrapper for Tcl Channels.
        [[r39704]] -- 
            Group several related Tcl command extensions and common services they
            may require together.
        [[r39809]] -- 
            Adaptor between `CTCLOjbectProcessor`
            and `CTCLProcessor`.
        [[r39876]] -- 
            Base class for building object oriented Tcl File event handlers.
        [[r39962]] -- 
            Object oriented interface to Tcl's hash table functions.
        [[r40093]] -- 
            Encapsulation of an entry in a Tcl Hash table as encapsulated
            in `CTCLHashTable`
[[r40161]] -- 
            Iterator for visiting all elements of a `CTCLHashTable`
[[r40257]] -- 
            Allows the establishment of an executable object that
            can be scheduled to be invoked when the Tcl/Tk intperpreter
            has no events that require processing.
        [[r40318]] -- 
            Base class for a command that lives in a `CTCLCommandPackage`
[[r40379]] -- 
            Provide an object oriented interace to the Tcl interpreter result.
        [[r40490]] -- 
            Provide a wrapper for the Tcl_DString data type
            and its API
        [[r40707]] -- 
            Abstract base class for C++ objects attached to timer events.
        [[r40777]] -- Run Tcl with event loop.[[r40881]] -- Accept commands on a Tcl channel from the event loop.[[r41093]] -- Event driven command input on stdin/stdout[[r41157]] -- Listener for a Tcl server.[[r41285]] -- Channel commander that is a server instance for `CTCLServer`[[r41358]] -- Provide common functionality for a set of
                related commands.[[r41420]] -- Base class for commands living in a
                    `CTCLObjectPackage`
[[r41520]] -- Hold a configuration[[r42243]] -- Base class for objects tht have a configuration.[[r42463]] -- Abstract base class for the exception class hierarchy.[[r42550]] -- Exceptions that wrap the Unix `errno`[[r42627]] -- Reports and exception for a value out of allowed range.[[r42765]] -- Exception for invalid state transitions.[[r42864]] -- I/O error on a C++ stream.[[r43027]] -- Report errors in universal resource identifiers (uri)s.[[r43212]] -- Exceptions for synchronization class abuse.[[r43347]] -- Report invalid function arguments.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| vmusbcaenupgrader | Up | CRingMaster |
