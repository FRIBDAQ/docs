|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

<a name="man-3daq"></a># VIII. 3daq

**Table of Contents**[[r24957]] -- RingMaster access.[[r25199]] -- Remote Ring Access[[r25395]] -- Provide zero copy access to low level ring buffers.[[r25454]] -- Low level ring buffer primitives[[r26274]] -- Encapsulates an item in a ring buffer.[[r26764]] -- Encapsulate ring buffer scaler items.[[r27261]] -- Encapsulate a ring buffer state change item.[[r27703]] -- Encapsulate ring items that are lists of text strings.[[r28065]] -- Response to trigger.[[r28261]] -- Provides statistics regarding the number of events produced.[[r28623]] -- Encapsulate a EVB_FRAGMENT ring item
         [[r28938]] -- Event fragment likley not containing a ring item[[r29036]] -- Describe the format of a stream of ringitems.[[r29290]] -- Reports event building parameters.[[r29558]] -- Abnormal end of run.[[r29772]] -- Base class for predicates that select items from
            ring buffers.[[r30114]] -- Select all ring items except some.[[r30300]] -- Only accept specified ring item types.[[r30475]] -- Format of ring items.[[r31001]] -- Functions to create ring items.[[r32407]] -- Abstract base class of data source for ring items.[[r32459]] -- Ringbuffer data source for ring items.[[r32538]] -- Ring item data source from a file[[r32605]] -- Create data sources given a URI[[r32672]] -- Upcast ring items to specific ring item objects.[[r32775]] -- Abstract base class for data sinks.[[r32866]] -- Data sink to a disk file.[[r33008]] -- Data sink that writes to a `CRingBuffer`
[[r33109]] -- Create an appropriate CDataSink object[[r33175]] -- Provides zero copy, low level consumer access to ring buffers[[r33432]] -- Wrappers for userspace USB library.[[r33475]] -- Report errors from libUSB1[[r33502]] -- Encapsulate low level USB context[[r33552]] -- Provide information about a USB device.[[r33698]] -- I/O object for a USB device[[r33949]] -- Utility methods for JTEC/Wiener XXUSB controllers[[r34265]] -- Top Level Logbook C++ API[[r35021]] -- Encapsulate a person registered in a logbook.[[r35159]] -- Encapsulates shifts in logbook databases[[r35332]] -- Encapsulates runs from logbooks.[[r35823]] -- Encapsulate logbook notes.[[r36151]] -- Define event builder fragment structures.[[r36378]] -- Framework event builder client application.[[r36532]] -- Event builder client framework.[[r36598]] -- Client of the event orderer[[r36819]] -- Iterator for event built data.[[r37030]] -- Provide a C++ interface to the server port manager daemon.[[r37187]] -- Report errors conditions in port manager transactions[[r37343]] -- Support the Hytec NADC 2530 Peak sensing ADC.[[r37815]] -- Support for the CAEN 32 bit digitizers[[r38620]] -- CES CBD 8210 CAMAC branch highway driver (obsolete)[[r38998]] -- Support for the CAEN V1190 and V1290
                    multihit, complicated TDC.[[r41390]] -- Support the CCAENV560 non-latching scaler.[[r41564]] -- Support driver for the CAEN V820/V830 latching scaler module.[[r42131]] -- Software support for the CAEN V977 I/O register.[[r42540]] -- Support software for the LeCroy LRS 2551 12 channel CAMAC scaler[[r42660]] -- High level support software for the 32 channel LeCroy LRS 4434 CAMAC scaler module[[r42782]] -- Provide computer busy status support for the BiRA CAMAC
                NIM out module.
            [[r42900]] -- Trigger module for the CES CBD 8210 VME CAMAC Parallel Branch Highway Driver
            [[r42964]] -- Manages CAMAC memory maps.[[r43056]] -- Provide support for a generic CAMAC module.[[r43440]] -- Provides low level support for the BiRa CAMAC Nim output module.[[r43539]] -- Encapsulation of a BiRa 1302 CAMAC controller via CES CBS8210.[[r43889]] -- Support for the SIS 3600 VME latch module.[[r44358]] -- Low level support for SIS 3820 32 channel latching scaler module[[r45074]] -- Abstract base class for reading scalers into a vector[[r45191]] -- Abstract base class for status modules.[[r45266]] -- Abstract base class for triggers[[r45304]] -- Pointer like object for accessing the VME[[r45658]] -- High level support for the LeCroy LRS 1151 VME scaler.[[r45755]] -- Implement a status module using the CAEN V262 module.[[r45849]] -- VME trigger class based on the CAEN V262 I/O module.[[r45910]] -- [[r46263]] -- Support for the CAEN V262 I/O register module.[[r46420]] -- Exception that can be thrown in the event of memory mapping errors.[[r46465]] -- Low level support for the BiRa VME nim output module[[r46749]] -- Convenience base class for implementing VME module support[[r47057]] -- Low Level support for the SIS 3300 Flash ADC module[[r47800]] -- Base class for primitive filters[[r47984]] -- A composite filter composed of primitive filters[[r48204]] -- Ring item filter application class.[[r48277]] -- Integer byte order conversions[[r48473]] -- Abstract base class for thread objects.[[r48616]] -- Thread with synchronized initialization[[r48711]] -- Wait queue for threads[[r48819]] -- Provide Critical Regions, Monitors[[r48996]] -- C++ encapsulation of pthread mutexes.[[r49227]] -- Simple, safe critical section[[r49260]] -- Encapsulate POSIX condition variables.[[r49571]] -- Provide entry/exit guards for object critical regions.[[r49637]] -- Templated class for safe inter-thread messaging.[[r49834]] -- Abstract base authenticator class.[[r49948]] -- Authenticate against a stored password.[[r50146]] -- Authenticate against a unix user name and password.[[r50367]] -- Authenticate against a Tcl List.[[r50475]] -- Authenticate against a list of allowed credentials.[[r50627]] -- Authenticate from a list of TCP/IP hosts[[r50817]] -- Base class for security interactions.[[r50996]] -- Provide an interactor that processes strings.[[r51167]] -- Interact with  file descriptor[[r51303]] -- Separate prompt and input interactors.[[r51438]] -- Parse Uniform Resource Identifiers (URI)[[r51596]] -- Generate license/author credits.[[r51702]] -- Binary I/O operations.[[r51826]] -- Operating system interfaces.[[r52011]] -- class description[[r52380]] -- Simple binary buffered output class with flush.[[r52476]] -- ABC for reading blocks of ring items from a source.[[r52575]] -- CRingBlockreader that reads from file.[[r52612]] -- Subsecond measurement of elapsed times.[[r52628]] -- Encapsulation of a socket file descriptor.[[r53482]] -- class description[[r53601]] -- Exception thrown for TCP/IP connection failures.[[r53723]] -- Exception thrown when connection to peer is lost[[r53833]] -- CTCPNoSuchHost[[r53968]] -- Exception thrown if a nonexistent service is referenced[[r54056]] -- 
            Base class for TCL/Tk applications.
        [[r54109]] -- 
            Class for reporting exceptional conditions in Tcl applications
            via the C++ try/catch mechanism.
        [[r54262]] -- 
            Encapsulate a Tcl interpreter.
        [[r54490]] -- 
            Base class for objects that are associated with a Tcl Interpreter.
        [[r54579]] -- 
            Provide access to Tcl List parsing.
        [[r54698]] -- 
            Encapsulate Tcl Dual ported objects.
        [[r54939]] -- 
            Abstract base class to encapsulate the Tcl object command interface exposed by
            `Tcl_CreateObjCommand`.
        [[r55042]] -- 
            Encapsulate Tcl interpreter variables.
        [[r55247]] -- 
            Provide `argc`, `argv`
            extension commands to Tcl.
        [[r55446]] -- 
            Provide a C++ abstraction wrapper for Tcl Channels.
        [[r55626]] -- 
            Group several related Tcl command extensions and common services they
            may require together.
        [[r55741]] -- 
            Adaptor between `CTCLOjbectProcessor`
            and `CTCLProcessor`.
        [[r55818]] -- 
            Base class for building object oriented Tcl File event handlers.
        [[r55914]] -- 
            Object oriented interface to Tcl's hash table functions.
        [[r56055]] -- 
            Encapsulation of an entry in a Tcl Hash table as encapsulated
            in `CTCLHashTable`
[[r56133]] -- 
            Iterator for visiting all elements of a `CTCLHashTable`
[[r56239]] -- 
            Allows the establishment of an executable object that
            can be scheduled to be invoked when the Tcl/Tk intperpreter
            has no events that require processing.
        [[r56310]] -- 
            Base class for a command that lives in a `CTCLCommandPackage`
[[r56381]] -- 
            Provide an object oriented interace to the Tcl interpreter result.
        [[r56502]] -- 
            Provide a wrapper for the Tcl_DString data type
            and its API
        [[r56729]] -- 
            Abstract base class for C++ objects attached to timer events.
        [[r56809]] -- Run Tcl with event loop.[[r56923]] -- Accept commands on a Tcl channel from the event loop.[[r57145]] -- Event driven command input on stdin/stdout[[r57219]] -- Listener for a Tcl server.[[r57357]] -- Channel commander that is a server instance for `CTCLServer`[[r57440]] -- Provide common functionality for a set of
                related commands.[[r57512]] -- Base class for commands living in a
                    `CTCLObjectPackage`
[[r57622]] -- Hold a configuration[[r58355]] -- Base class for objects tht have a configuration.[[r58585]] -- Abstract base class for the exception class hierarchy.[[r58682]] -- Exceptions that wrap the Unix `errno`[[r58769]] -- Reports and exception for a value out of allowed range.[[r58917]] -- Exception for invalid state transitions.[[r59026]] -- I/O error on a C++ stream.[[r59199]] -- Report errors in universal resource identifiers (uri)s.[[r59394]] -- Exceptions for synchronization class abuse.[[r59539]] -- Report invalid function arguments.[[r59683]] -- Suport dynamic configuration of Pixie16 modules via DDASReadout Server.[[r59873]] -- Low Level Access To Digitizers[[r60382]] -- Provide compile time checked API to CAEN Nextgen digitizers DPP-PHA[[r64088]] -- Encapsulate module configuration for CAEN Nextgen digitizers[[r65374]] -- Tcl scripted configuration.[[r65505]] -- Event Segment configured with Tcl[[r65591]] -- Event segment for single VX2750 DPP-PHA module[[r65664]] -- Manage readout triggers.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| vmusbcaenupgrader | Up | CRingMaster |
