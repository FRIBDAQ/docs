|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

<a name="man-3daq"></a># VIII. 3daq

**Table of Contents**[[r17620]] -- RingMaster access.[[r17862]] -- Remote Ring Access[[r18058]] -- Low level ring buffer primitives[[r18878]] -- Encapsulates an item in a ring buffer.[[r19355]] -- Encapsulate ring buffer scaler items.[[r19801]] -- Encapsulate a ring buffer state change item.[[r20206]] -- Encapsulate ring items that are lists of text strings.[[r20532]] -- Response to trigger.[[r20728]] -- Provides statistics regarding the number of events produced.[[r21055]] -- Encapsulate a EVB_FRAGMENT ring item
         [[r21370]] -- Event fragment likley not containing a ring item[[r21468]] -- Describe the format of a stream of ringitems.[[r21721]] -- Reports event building parameters.[[r21989]] -- Abnormal end of run.[[r22203]] -- Base class for predicates that select items from
            ring buffers.[[r22545]] -- Select all ring items except some.[[r22731]] -- Only accept specified ring item types.[[r22906]] -- Format of ring items.[[r23405]] -- Functions to create ring items.[[r24325]] -- Abstract base class of data source for ring items.[[r24377]] -- Ringbuffer data source for ring items.[[r24456]] -- Ring item data source from a file[[r24523]] -- Create data sources given a URI[[r24590]] -- Upcast ring items to specific ring item objects.[[r24693]] -- Abstract base class for data sinks.[[r24784]] -- Data sink to a disk file.[[r24926]] -- Data sink that writes to a `CRingBuffer`
[[r25027]] -- Create an appropriate CDataSink object[[r25093]] -- Framework event builder client application.[[r25247]] -- Event builder client framework.[[r25313]] -- Client of the event orderer[[r25534]] -- Iterator for event built data.[[r25746]] -- Provide a C++ interface to the server port manager daemon.[[r25903]] -- Report errors conditions in port manager transactions[[r26059]] -- Support the Hytec NADC 2530 Peak sensing ADC.[[r26531]] -- Support for the CAEN 32 bit digitizers[[r27336]] -- CES CBD 8210 CAMAC branch highway driver (obsolete)[[r27714]] -- Support for the CAEN V1190 and V1290
                    multihit, complicated TDC.[[r30106]] -- Support the CCAENV560 non-latching scaler.[[r30280]] -- Support driver for the CAEN V820/V830 latching scaler module.[[r30847]] -- Software support for the CAEN V977 I/O register.[[r31256]] -- Support software for the LeCroy LRS 2551 12 channel CAMAC scaler[[r31376]] -- High level support software for the 32 channel LeCroy LRS 4434 CAMAC scaler module[[r31498]] -- Provide computer busy status support for the BiRA CAMAC
                NIM out module.
            [[r31616]] -- Trigger module for the CES CBD 8210 VME CAMAC Parallel Branch Highway Driver
            [[r31680]] -- Manages CAMAC memory maps.[[r31772]] -- Provide support for a generic CAMAC module.[[r32156]] -- Provides low level support for the BiRa CAMAC Nim output module.[[r32255]] -- Encapsulation of a BiRa 1302 CAMAC controller via CES CBS8210.[[r32605]] -- Support for the SIS 3600 VME latch module.[[r33074]] -- Low level support for SIS 3820 32 channel latching scaler module[[r33790]] -- Abstract base class for reading scalers into a vector[[r33907]] -- Abstract base class for status modules.[[r33982]] -- Abstract base class for triggers[[r34020]] -- Pointer like object for accessing the VME[[r34374]] -- High level support for the LeCroy LRS 1151 VME scaler.[[r34471]] -- Implement a status module using the CAEN V262 module.[[r34565]] -- VME trigger class based on the CAEN V262 I/O module.[[r34626]] -- [[r34979]] -- Support for the CAEN V262 I/O register module.[[r35136]] -- Exception that can be thrown in the event of memory mapping errors.[[r35181]] -- Low level support for the BiRa VME nim output module[[r35465]] -- Convenience base class for implementing VME module support[[r35773]] -- Low Level support for the SIS 3300 Flash ADC module[[r36516]] -- Base class for primitive filters[[r36700]] -- A composite filter composed of primitive filters[[r36920]] -- Integer byte order conversions[[r37116]] -- Abstract base class for thread objects.[[r37259]] -- Thread with synchronized initialization[[r37354]] -- Wait queue for threads[[r37462]] -- Provide Critical Regions, Monitors[[r37639]] -- C++ encapsulation of pthread mutexes.[[r37870]] -- Simple, safe critical section[[r37903]] -- Encapsulate POSIX condition variables.[[r38214]] -- Provide entry/exit guards for object critical regions.[[r38280]] -- Templated class for safe inter-thread messaging.[[r38477]] -- Abstract base authenticator class.[[r38591]] -- Authenticate against a stored password.[[r38789]] -- Authenticate against a unix user name and password.[[r39010]] -- Authenticate against a Tcl List.[[r39118]] -- Authenticate against a list of allowed credentials.[[r39270]] -- Authenticate from a list of TCP/IP hosts[[r39460]] -- Base class for security interactions.[[r39639]] -- Provide an interactor that processes strings.[[r39810]] -- Interact with  file descriptor[[r39946]] -- Separate prompt and input interactors.[[r40081]] -- Parse Uniform Resource Identifiers (URI)[[r40239]] -- Generate license/author credits.[[r40345]] -- Binary I/O operations.[[r40469]] -- Operating system interfaces.[[r40654]] -- class description[[r41023]] -- Encapsulation of a socket file descriptor.[[r41877]] -- class description[[r41996]] -- Exception thrown for TCP/IP connection failures.[[r42118]] -- Exception thrown when connection to peer is lost[[r42228]] -- CTCPNoSuchHost[[r42363]] -- Exception thrown if a nonexistent service is referenced[[r42451]] -- 
            Base class for TCL/Tk applications.
        [[r42494]] -- 
            Class for reporting exceptional conditions in Tcl applications
            via the C++ try/catch mechanism.
        [[r42637]] -- 
            Encapsulate a Tcl interpreter.
        [[r42855]] -- 
            Base class for objects that are associated with a Tcl Interpreter.
        [[r42934]] -- 
            Provide access to Tcl List parsing.
        [[r43043]] -- 
            Encapsulate Tcl Dual ported objects.
        [[r43274]] -- 
            Abstract base class to encapsulate the Tcl object command interface exposed by
            `Tcl_CreateObjCommand`.
        [[r43367]] -- 
            Encapsulate Tcl interpreter variables.
        [[r43562]] -- 
            Provide `argc`, `argv`
            extension commands to Tcl.
        [[r43751]] -- 
            Provide a C++ abstraction wrapper for Tcl Channels.
        [[r43921]] -- 
            Group several related Tcl command extensions and common services they
            may require together.
        [[r44026]] -- 
            Adaptor between `CTCLOjbectProcessor`
            and `CTCLProcessor`.
        [[r44093]] -- 
            Base class for building object oriented Tcl File event handlers.
        [[r44179]] -- 
            Object oriented interface to Tcl's hash table functions.
        [[r44310]] -- 
            Encapsulation of an entry in a Tcl Hash table as encapsulated
            in `CTCLHashTable`
[[r44378]] -- 
            Iterator for visiting all elements of a `CTCLHashTable`
[[r44474]] -- 
            Allows the establishment of an executable object that
            can be scheduled to be invoked when the Tcl/Tk intperpreter
            has no events that require processing.
        [[r44535]] -- 
            Base class for a command that lives in a `CTCLCommandPackage`
[[r44596]] -- 
            Provide an object oriented interace to the Tcl interpreter result.
        [[r44707]] -- 
            Provide a wrapper for the Tcl_DString data type
            and its API
        [[r44924]] -- 
            Abstract base class for C++ objects attached to timer events.
        [[r44994]] -- Run Tcl with event loop.[[r45098]] -- Accept commands on a Tcl channel from the event loop.[[r45310]] -- Event driven command input on stdin/stdout[[r45374]] -- Listener for a Tcl server.[[r45502]] -- Channel commander that is a server instance for `CTCLServer`[[r45575]] -- Provide common functionality for a set of
                related commands.[[r45637]] -- Base class for commands living in a
                    `CTCLObjectPackage`
[[r45737]] -- Hold a configuration[[r46460]] -- Base class for objects tht have a configuration.[[r46680]] -- Abstract base class for the exception class hierarchy.[[r46767]] -- Exceptions that wrap the Unix `errno`[[r46844]] -- Reports and exception for a value out of allowed range.[[r46982]] -- Exception for invalid state transitions.[[r47081]] -- I/O error on a C++ stream.[[r47244]] -- Report errors in universal resource identifiers (uri)s.[[r47429]] -- Exceptions for synchronization class abuse.[[r47564]] -- Report invalid function arguments.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| vmusbcaenupgrader | Up | CRingMaster |
