|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

<a name="man-3daq"></a># VIII. 3daq

**Table of Contents**[[r16720]] -- RingMaster access.[[r16962]] -- Remote Ring Access[[r17158]] -- Low level ring buffer primitives[[r17978]] -- Encapsulates an item in a ring buffer.[[r18455]] -- Encapsulate ring buffer scaler items.[[r18901]] -- Encapsulate a ring buffer state change item.[[r19306]] -- Encapsulate ring items that are lists of text strings.[[r19632]] -- Response to trigger.[[r19828]] -- Provides statistics regarding the number of events produced.[[r20155]] -- Encapsulate a EVB_FRAGMENT ring item
         [[r20470]] -- Event fragment likley not containing a ring item[[r20568]] -- Describe the format of a stream of ringitems.[[r20821]] -- Reports event building parameters.[[r21089]] -- Abnormal end of run.[[r21303]] -- Base class for predicates that select items from
            ring buffers.[[r21645]] -- Select all ring items except some.[[r21831]] -- Only accept specified ring item types.[[r22006]] -- Format of ring items.[[r22505]] -- Functions to create ring items.[[r23425]] -- Abstract base class of data source for ring items.[[r23477]] -- Ringbuffer data source for ring items.[[r23556]] -- Ring item data source from a file[[r23623]] -- Create data sources given a URI[[r23690]] -- Upcast ring items to specific ring item objects.[[r23793]] -- Abstract base class for data sinks.[[r23884]] -- Data sink to a disk file.[[r24026]] -- Data sink that writes to a `CRingBuffer`
[[r24127]] -- Create an appropriate CDataSink object[[r24193]] -- Framework event builder client application.[[r24347]] -- Event builder client framework.[[r24413]] -- Client of the event orderer[[r24634]] -- Iterator for event built data.[[r24845]] -- Provide a C++ interface to the server port manager daemon.[[r25002]] -- Report errors conditions in port manager transactions[[r25158]] -- Support the Hytec NADC 2530 Peak sensing ADC.[[r25630]] -- Support for the CAEN 32 bit digitizers[[r26435]] -- CES CBD 8210 CAMAC branch highway driver (obsolete)[[r26813]] -- Support for the CAEN V1190 and V1290
                    multihit, complicated TDC.[[r29205]] -- Support the CCAENV560 non-latching scaler.[[r29379]] -- Support driver for the CAEN V820/V830 latching scaler module.[[r29946]] -- Software support for the CAEN V977 I/O register.[[r30355]] -- Support software for the LeCroy LRS 2551 12 channel CAMAC scaler[[r30475]] -- High level support software for the 32 channel LeCroy LRS 4434 CAMAC scaler module[[r30597]] -- Provide computer busy status support for the BiRA CAMAC
                NIM out module.
            [[r30715]] -- Trigger module for the CES CBD 8210 VME CAMAC Parallel Branch Highway Driver
            [[r30779]] -- Manages CAMAC memory maps.[[r30871]] -- Provide support for a generic CAMAC module.[[r31255]] -- Provides low level support for the BiRa CAMAC Nim output module.[[r31354]] -- Encapsulation of a BiRa 1302 CAMAC controller via CES CBS8210.[[r31704]] -- Support for the SIS 3600 VME latch module.[[r32173]] -- Low level support for SIS 3820 32 channel latching scaler module[[r32889]] -- Abstract base class for reading scalers into a vector[[r33006]] -- Abstract base class for status modules.[[r33081]] -- Abstract base class for triggers[[r33119]] -- Pointer like object for accessing the VME[[r33473]] -- High level support for the LeCroy LRS 1151 VME scaler.[[r33570]] -- Implement a status module using the CAEN V262 module.[[r33664]] -- VME trigger class based on the CAEN V262 I/O module.[[r33725]] -- [[r34078]] -- Support for the CAEN V262 I/O register module.[[r34235]] -- Exception that can be thrown in the event of memory mapping errors.[[r34280]] -- Low level support for the BiRa VME nim output module[[r34564]] -- Convenience base class for implementing VME module support[[r34872]] -- Low Level support for the SIS 3300 Flash ADC module[[r35615]] -- Integer byte order conversions[[r35811]] -- Abstract base class for thread objects.[[r35954]] -- Thread with synchronized initialization[[r36049]] -- Wait queue for threads[[r36157]] -- Provide Critical Regions, Monitors[[r36334]] -- C++ encapsulation of pthread mutexes.[[r36565]] -- Simple, safe critical section[[r36598]] -- Encapsulate POSIX condition variables.[[r36909]] -- Provide entry/exit guards for object critical regions.[[r36975]] -- Templated class for safe inter-thread messaging.[[r37172]] -- Abstract base authenticator class.[[r37286]] -- Authenticate against a stored password.[[r37484]] -- Authenticate against a unix user name and password.[[r37705]] -- Authenticate against a Tcl List.[[r37813]] -- Authenticate against a list of allowed credentials.[[r37965]] -- Authenticate from a list of TCP/IP hosts[[r38155]] -- Base class for security interactions.[[r38334]] -- Provide an interactor that processes strings.[[r38505]] -- Interact with  file descriptor[[r38641]] -- Separate prompt and input interactors.[[r38776]] -- Parse Uniform Resource Identifiers (URI)[[r38934]] -- Generate license/author credits.[[r39040]] -- Binary I/O operations.[[r39164]] -- Operating system interfaces.[[r39349]] -- class description[[r39718]] -- Encapsulation of a socket file descriptor.[[r40572]] -- class description[[r40691]] -- Exception thrown for TCP/IP connection failures.[[r40813]] -- Exception thrown when connection to peer is lost[[r40923]] -- CTCPNoSuchHost[[r41058]] -- Exception thrown if a nonexistent service is referenced[[r41146]] -- 
            Base class for TCL/Tk applications.
        [[r41199]] -- 
            Class for reporting exceptional conditions in Tcl applications
            via the C++ try/catch mechanism.
        [[r41352]] -- 
            Encapsulate a Tcl interpreter.
        [[r41580]] -- 
            Base class for objects that are associated with a Tcl Interpreter.
        [[r41669]] -- 
            Provide access to Tcl List parsing.
        [[r41788]] -- 
            Encapsulate Tcl Dual ported objects.
        [[r42029]] -- 
            Abstract base class to encapsulate the Tcl object command interface exposed by
            `Tcl_CreateObjCommand`.
        [[r42132]] -- 
            Encapsulate Tcl interpreter variables.
        [[r42337]] -- 
            Provide `argc`, `argv`
            extension commands to Tcl.
        [[r42536]] -- 
            Provide a C++ abstraction wrapper for Tcl Channels.
        [[r42716]] -- 
            Group several related Tcl command extensions and common services they
            may require together.
        [[r42831]] -- 
            Adaptor between `CTCLOjbectProcessor`
            and `CTCLProcessor`.
        [[r42908]] -- 
            Base class for building object oriented Tcl File event handlers.
        [[r43004]] -- 
            Object oriented interface to Tcl's hash table functions.
        [[r43145]] -- 
            Encapsulation of an entry in a Tcl Hash table as encapsulated
            in `CTCLHashTable`
[[r43223]] -- 
            Iterator for visiting all elements of a `CTCLHashTable`
[[r43329]] -- 
            Allows the establishment of an executable object that
            can be scheduled to be invoked when the Tcl/Tk intperpreter
            has no events that require processing.
        [[r43400]] -- 
            Base class for a command that lives in a `CTCLCommandPackage`
[[r43471]] -- 
            Provide an object oriented interace to the Tcl interpreter result.
        [[r43592]] -- 
            Provide a wrapper for the Tcl_DString data type
            and its API
        [[r43819]] -- 
            Abstract base class for C++ objects attached to timer events.
        [[r43899]] -- Run Tcl with event loop.[[r44013]] -- Accept commands on a Tcl channel from the event loop.[[r44235]] -- Event driven command input on stdin/stdout[[r44309]] -- Listener for a Tcl server.[[r44447]] -- Channel commander that is a server instance for `CTCLServer`[[r44530]] -- Provide common functionality for a set of
                related commands.[[r44602]] -- Base class for commands living in a
                    `CTCLObjectPackage`
[[r44712]] -- Hold a configuration[[r45445]] -- Base class for objects tht have a configuration.[[r45675]] -- Abstract base class for the exception class hierarchy.[[r45772]] -- Exceptions that wrap the Unix `errno`[[r45859]] -- Reports and exception for a value out of allowed range.[[r46007]] -- Exception for invalid state transitions.[[r46116]] -- I/O error on a C++ stream.[[r46289]] -- Report errors in universal resource identifiers (uri)s.[[r46484]] -- Exceptions for synchronization class abuse.[[r46629]] -- Report invalid function arguments.[[r46773]] -- Suport dynamic configuration of Pixie16 modules via DDASReadout Server.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| vmusbcaenupgrader | Up | CRingMaster |
