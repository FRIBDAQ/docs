|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

<a name="man-3daq"></a># VIII. 3daq

**Table of Contents**[[r16912]] -- RingMaster access.[[r17154]] -- Remote Ring Access[[r17350]] -- Low level ring buffer primitives[[r18170]] -- Encapsulates an item in a ring buffer.[[r18647]] -- Encapsulate ring buffer scaler items.[[r19093]] -- Encapsulate a ring buffer state change item.[[r19498]] -- Encapsulate ring items that are lists of text strings.[[r19824]] -- Response to trigger.[[r20020]] -- Provides statistics regarding the number of events produced.[[r20347]] -- Encapsulate a EVB_FRAGMENT ring item
         [[r20662]] -- Event fragment likley not containing a ring item[[r20760]] -- Describe the format of a stream of ringitems.[[r21013]] -- Reports event building parameters.[[r21281]] -- Abnormal end of run.[[r21495]] -- Base class for predicates that select items from
            ring buffers.[[r21837]] -- Select all ring items except some.[[r22023]] -- Only accept specified ring item types.[[r22198]] -- Format of ring items.[[r22697]] -- Functions to create ring items.[[r23617]] -- Abstract base class of data source for ring items.[[r23669]] -- Ringbuffer data source for ring items.[[r23748]] -- Ring item data source from a file[[r23815]] -- Create data sources given a URI[[r23882]] -- Upcast ring items to specific ring item objects.[[r23985]] -- Abstract base class for data sinks.[[r24076]] -- Data sink to a disk file.[[r24218]] -- Data sink that writes to a `CRingBuffer`
[[r24319]] -- Create an appropriate CDataSink object[[r24385]] -- Framework event builder client application.[[r24539]] -- Event builder client framework.[[r24605]] -- Client of the event orderer[[r24826]] -- Provide a C++ interface to the server port manager daemon.[[r24983]] -- Report errors conditions in port manager transactions[[r25139]] -- Support the Hytec NADC 2530 Peak sensing ADC.[[r25611]] -- Support for the CAEN 32 bit digitizers[[r26416]] -- CES CBD 8210 CAMAC branch highway driver (obsolete)[[r26794]] -- Support for the CAEN V1190 and V1290
                    multihit, complicated TDC.[[r29186]] -- Support the CCAENV560 non-latching scaler.[[r29360]] -- Support driver for the CAEN V820/V830 latching scaler module.[[r29927]] -- Software support for the CAEN V977 I/O register.[[r30336]] -- Support software for the LeCroy LRS 2551 12 channel CAMAC scaler[[r30456]] -- High level support software for the 32 channel LeCroy LRS 4434 CAMAC scaler module[[r30578]] -- Provide computer busy status support for the BiRA CAMAC
                NIM out module.
            [[r30696]] -- Trigger module for the CES CBD 8210 VME CAMAC Parallel Branch Highway Driver
            [[r30760]] -- Manages CAMAC memory maps.[[r30852]] -- Provide support for a generic CAMAC module.[[r31236]] -- Provides low level support for the BiRa CAMAC Nim output module.[[r31335]] -- Encapsulation of a BiRa 1302 CAMAC controller via CES CBS8210.[[r31685]] -- Support for the SIS 3600 VME latch module.[[r32154]] -- Low level support for SIS 3820 32 channel latching scaler module[[r32870]] -- Abstract base class for reading scalers into a vector[[r32987]] -- Abstract base class for status modules.[[r33062]] -- Abstract base class for triggers[[r33100]] -- Pointer like object for accessing the VME[[r33454]] -- High level support for the LeCroy LRS 1151 VME scaler.[[r33551]] -- Implement a status module using the CAEN V262 module.[[r33645]] -- VME trigger class based on the CAEN V262 I/O module.[[r33706]] -- [[r34059]] -- Support for the CAEN V262 I/O register module.[[r34216]] -- Exception that can be thrown in the event of memory mapping errors.[[r34261]] -- Low level support for the BiRa VME nim output module[[r34545]] -- Convenience base class for implementing VME module support[[r34853]] -- Low Level support for the SIS 3300 Flash ADC module[[r35596]] -- Base class for primitive filters[[r35780]] -- A composite filter composed of primitive filters[[r36000]] -- Integer byte order conversions[[r36196]] -- Abstract base class for thread objects.[[r36339]] -- Thread with synchronized initialization[[r36434]] -- Wait queue for threads[[r36542]] -- Provide Critical Regions, Monitors[[r36719]] -- C++ encapsulation of pthread mutexes.[[r36950]] -- Simple, safe critical section[[r36983]] -- Encapsulate POSIX condition variables.[[r37294]] -- Provide entry/exit guards for object critical regions.[[r37360]] -- Templated class for safe inter-thread messaging.[[r37557]] -- Abstract base authenticator class.[[r37671]] -- Authenticate against a stored password.[[r37869]] -- Authenticate against a unix user name and password.[[r38090]] -- Authenticate against a Tcl List.[[r38198]] -- Authenticate against a list of allowed credentials.[[r38350]] -- Authenticate from a list of TCP/IP hosts[[r38540]] -- Base class for security interactions.[[r38719]] -- Provide an interactor that processes strings.[[r38890]] -- Interact with  file descriptor[[r39026]] -- Separate prompt and input interactors.[[r39161]] -- Parse Uniform Resource Identifiers (URI)[[r39319]] -- Generate license/author credits.[[r39425]] -- Binary I/O operations.[[r39549]] -- Operating system interfaces.[[r39734]] -- class description[[r40103]] -- Encapsulation of a socket file descriptor.[[r40957]] -- class description[[r41076]] -- Exception thrown for TCP/IP connection failures.[[r41198]] -- Exception thrown when connection to peer is lost[[r41308]] -- CTCPNoSuchHost[[r41443]] -- Exception thrown if a nonexistent service is referenced[[r41531]] -- 
            Base class for TCL/Tk applications.
        [[r41574]] -- 
            Class for reporting exceptional conditions in Tcl applications
            via the C++ try/catch mechanism.
        [[r41717]] -- 
            Encapsulate a Tcl interpreter.
        [[r41935]] -- 
            Base class for objects that are associated with a Tcl Interpreter.
        [[r42014]] -- 
            Provide access to Tcl List parsing.
        [[r42123]] -- 
            Encapsulate Tcl Dual ported objects.
        [[r42354]] -- 
            Abstract base class to encapsulate the Tcl object command interface exposed by
            `Tcl_CreateObjCommand`.
        [[r42447]] -- 
            Encapsulate Tcl interpreter variables.
        [[r42642]] -- 
            Provide `argc`, `argv`
            extension commands to Tcl.
        [[r42831]] -- 
            Provide a C++ abstraction wrapper for Tcl Channels.
        [[r43001]] -- 
            Group several related Tcl command extensions and common services they
            may require together.
        [[r43106]] -- 
            Adaptor between `CTCLOjbectProcessor`
            and `CTCLProcessor`.
        [[r43173]] -- 
            Base class for building object oriented Tcl File event handlers.
        [[r43259]] -- 
            Object oriented interface to Tcl's hash table functions.
        [[r43390]] -- 
            Encapsulation of an entry in a Tcl Hash table as encapsulated
            in `CTCLHashTable`
[[r43458]] -- 
            Iterator for visiting all elements of a `CTCLHashTable`
[[r43554]] -- 
            Allows the establishment of an executable object that
            can be scheduled to be invoked when the Tcl/Tk intperpreter
            has no events that require processing.
        [[r43615]] -- 
            Base class for a command that lives in a `CTCLCommandPackage`
[[r43676]] -- 
            Provide an object oriented interace to the Tcl interpreter result.
        [[r43787]] -- 
            Provide a wrapper for the Tcl_DString data type
            and its API
        [[r44004]] -- 
            Abstract base class for C++ objects attached to timer events.
        [[r44074]] -- Run Tcl with event loop.[[r44178]] -- Accept commands on a Tcl channel from the event loop.[[r44390]] -- Event driven command input on stdin/stdout[[r44454]] -- Listener for a Tcl server.[[r44582]] -- Channel commander that is a server instance for `CTCLServer`[[r44655]] -- Provide common functionality for a set of
                related commands.[[r44717]] -- Base class for commands living in a
                    `CTCLObjectPackage`
[[r44817]] -- Hold a configuration[[r45540]] -- Base class for objects tht have a configuration.[[r45760]] -- Abstract base class for the exception class hierarchy.[[r45847]] -- Exceptions that wrap the Unix `errno`[[r45924]] -- Reports and exception for a value out of allowed range.[[r46062]] -- Exception for invalid state transitions.[[r46161]] -- I/O error on a C++ stream.[[r46324]] -- Report errors in universal resource identifiers (uri)s.[[r46509]] -- Exceptions for synchronization class abuse.[[r46644]] -- Report invalid function arguments.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| vmusbcaenupgrader | Up | CRingMaster |
