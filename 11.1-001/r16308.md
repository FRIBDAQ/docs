|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

<a name="man-3daq"></a># VIII. 3daq

**Table of Contents**[[r16310]] -- RingMaster access.[[r16549]] -- Remote Ring Access[[r16742]] -- Low level ring buffer primitives[[r17552]] -- Encapsulates an item in a ring buffer.[[r18019]] -- Encapsulate ring buffer scaler items.[[r18455]] -- Encapsulate a ring buffer state change item.[[r18850]] -- Encapsulate ring items that are lists of text strings.[[r19166]] -- Response to trigger.[[r19352]] -- Provides statistics regarding the number of events produced.[[r19669]] -- Encapsulate a EVB_FRAGMENT ring item
         [[r19974]] -- Event fragment likley not containing a ring item[[r20062]] -- Describe the format of a stream of ringitems.[[r20305]] -- Reports event building parameters.[[r20563]] -- Abnormal end of run.[[r20775]] -- Base class for predicates that select items from
            ring buffers.[[r21107]] -- Select all ring items except some.[[r21283]] -- Only accept specified ring item types.[[r21448]] -- Format of ring items.[[r21937]] -- Functions to create ring items.[[r22847]] -- Abstract base class of data source for ring items.[[r22889]] -- Ringbuffer data source for ring items.[[r22958]] -- Ring item data source from a file[[r23015]] -- Create data sources given a URI[[r23072]] -- Upcast ring items to specific ring item objects.[[r23165]] -- Abstract base class for data sinks.[[r23254]] -- Data sink to a disk file.[[r23394]] -- Data sink that writes to a `CRingBuffer`
[[r23493]] -- Create an appropriate CDataSink object[[r23557]] -- Framework event builder client application.[[r23701]] -- Event builder client framework.[[r23757]] -- Client of the event orderer[[r23968]] -- Provide a C++ interface to the server port manager daemon.[[r24123]] -- Report errors conditions in port manager transactions[[r24277]] -- Support the Hytec NADC 2530 Peak sensing ADC.[[r24739]] -- Support for the CAEN 32 bit digitizers[[r25542]] -- CES CBD 8210 CAMAC branch highway driver (obsolete)[[r25910]] -- Support for the CAEN V1190 and V1290
                    multihit, complicated TDC.[[r28292]] -- Support the CCAENV560 non-latching scaler.[[r28456]] -- Support driver for the CAEN V820/V830 latching scaler module.[[r29013]] -- Software support for the CAEN V977 I/O register.[[r29412]] -- Support software for the LeCroy LRS 2551 12 channel CAMAC scaler[[r29522]] -- High level support software for the 32 channel LeCroy LRS 4434 CAMAC scaler module[[r29634]] -- Provide computer busy status support for the BiRA CAMAC
                NIM out module.
            [[r29742]] -- Trigger module for the CES CBD 8210 VME CAMAC Parallel Branch Highway Driver
            [[r29796]] -- Manages CAMAC memory maps.[[r29878]] -- Provide support for a generic CAMAC module.[[r30252]] -- Provides low level support for the BiRa CAMAC Nim output module.[[r30341]] -- Encapsulation of a BiRa 1302 CAMAC controller via CES CBS8210.[[r30681]] -- Support for the SIS 3600 VME latch module.[[r31140]] -- Low level support for SIS 3820 32 channel latching scaler module[[r31846]] -- Abstract base class for reading scalers into a vector[[r31953]] -- Abstract base class for status modules.[[r32018]] -- Abstract base class for triggers[[r32046]] -- Pointer like object for accessing the VME[[r32390]] -- High level support for the LeCroy LRS 1151 VME scaler.[[r32477]] -- Implement a status module using the CAEN V262 module.[[r32561]] -- VME trigger class based on the CAEN V262 I/O module.[[r32612]] -- [[r32955]] -- Support for the CAEN V262 I/O register module.[[r33102]] -- Exception that can be thrown in the event of memory mapping errors.[[r33137]] -- Low level support for the BiRa VME nim output module[[r33411]] -- Convenience base class for implementing VME module support[[r33709]] -- Low Level support for the SIS 3300 Flash ADC module[[r34442]] -- Base class for primitive filters[[r34624]] -- A composite filter composed of primitive filters[[r34842]] -- Integer byte order conversions[[r35028]] -- Abstract base class for thread objects.[[r35169]] -- Thread with synchronized initialization[[r35262]] -- Wait queue for threads[[r35360]] -- Provide Critical Regions, Monitors[[r35527]] -- C++ encapsulation of pthread mutexes.[[r35748]] -- Simple, safe critical section[[r35779]] -- Encapsulate POSIX condition variables.[[r36080]] -- Provide entry/exit guards for object critical regions.[[r36136]] -- Templated class for safe inter-thread messaging.[[r36323]] -- Abstract base authenticator class.[[r36427]] -- Authenticate against a stored password.[[r36615]] -- Authenticate against a unix user name and password.[[r36826]] -- Authenticate against a Tcl List.[[r36924]] -- Authenticate against a list of allowed credentials.[[r37066]] -- Authenticate from a list of TCP/IP hosts[[r37246]] -- Base class for security interactions.[[r37415]] -- Provide an interactor that processes strings.[[r37576]] -- Interact with  file descriptor[[r37702]] -- Separate prompt and input interactors.[[r37827]] -- Parse Uniform Resource Identifiers (URI)[[r37975]] -- Generate license/author credits.[[r38071]] -- Binary I/O operations.[[r38193]] -- Operating system interfaces.[[r38376]] -- class description[[r38735]] -- Encapsulation of a socket file descriptor.[[r39587]] -- class description[[r39704]] -- Exception thrown for TCP/IP connection failures.[[r39824]] -- Exception thrown when connection to peer is lost[[r39932]] -- CTCPNoSuchHost[[r40065]] -- Exception thrown if a nonexistent service is referenced[[r40151]] -- 
            Base class for TCL/Tk applications.
        [[r40194]] -- 
            Class for reporting exceptional conditions in Tcl applications
            via the C++ try/catch mechanism.
        [[r40337]] -- 
            Encapsulate a Tcl interpreter.
        [[r40555]] -- 
            Base class for objects that are associated with a Tcl Interpreter.
        [[r40634]] -- 
            Provide access to Tcl List parsing.
        [[r40743]] -- 
            Encapsulate Tcl Dual ported objects.
        [[r40974]] -- 
            Abstract base class to encapsulate the Tcl object command interface exposed by
            `Tcl_CreateObjCommand`.
        [[r41067]] -- 
            Encapsulate Tcl interpreter variables.
        [[r41262]] -- 
            Provide `argc`, `argv`
            extension commands to Tcl.
        [[r41451]] -- 
            Provide a C++ abstraction wrapper for Tcl Channels.
        [[r41621]] -- 
            Group several related Tcl command extensions and common services they
            may require together.
        [[r41726]] -- 
            Adaptor between `CTCLOjbectProcessor`
            and `CTCLProcessor`.
        [[r41793]] -- 
            Base class for building object oriented Tcl File event handlers.
        [[r41879]] -- 
            Object oriented interface to Tcl's hash table functions.
        [[r42010]] -- 
            Encapsulation of an entry in a Tcl Hash table as encapsulated
            in `CTCLHashTable`
[[r42078]] -- 
            Iterator for visiting all elements of a `CTCLHashTable`
[[r42174]] -- 
            Allows the establishment of an executable object that
            can be scheduled to be invoked when the Tcl/Tk intperpreter
            has no events that require processing.
        [[r42235]] -- 
            Base class for a command that lives in a `CTCLCommandPackage`
[[r42296]] -- 
            Provide an object oriented interace to the Tcl interpreter result.
        [[r42407]] -- 
            Provide a wrapper for the Tcl_DString data type
            and its API
        [[r42624]] -- 
            Abstract base class for C++ objects attached to timer events.
        [[r42694]] -- Run Tcl with event loop.[[r42798]] -- Accept commands on a Tcl channel from the event loop.[[r43010]] -- Event driven command input on stdin/stdout[[r43074]] -- Listener for a Tcl server.[[r43202]] -- Channel commander that is a server instance for `CTCLServer`[[r43275]] -- Provide common functionality for a set of
                related commands.[[r43337]] -- Base class for commands living in a
                    `CTCLObjectPackage`
[[r43437]] -- Hold a configuration[[r44160]] -- Base class for objects tht have a configuration.[[r44380]] -- Abstract base class for the exception class hierarchy.[[r44467]] -- Exceptions that wrap the Unix `errno`[[r44544]] -- Reports and exception for a value out of allowed range.[[r44682]] -- Exception for invalid state transitions.[[r44781]] -- I/O error on a C++ stream.[[r44944]] -- Report errors in universal resource identifiers (uri)s.[[r45129]] -- Exceptions for synchronization class abuse.[[r45264]] -- Report invalid function arguments.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| vmusbcaenupgrader | Up | CRingMaster |
