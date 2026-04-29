<a name="AEN1"></a># <a name="AEN1"></a>NSCL DAQ Software Documentation


---

- **Table of Contents**
- I. [[introduction|p3]]
  - 1. [[Introduction|c5]]
    - 1.1. [[How does the ring buffer data acquisition system work|c5#AEN15]]
    - 1.2. [[Overview of ring buffer utilities|x123]]
    - 1.3. [[Documentation roadmap|x180]]
- II. [[commands|p263]]
  - 2. [[The **ringbuffer** command|c265]]
  - 3. [[Ring piping utilities|c292]]
  - 4. [[Command line access to CAMAC via the SBS interface|c318]]
  - 5. [[Tcl access to the VME via the SBS interface|c342]]
    - 5.1. [[Incorporating Vme Tcl in your scripts|c342#AEN357]]
    - 5.2. [[Sample programs that use the package|x377]]
- III. [[utilities|p384]]
  - 6. [[glom|c386]]
  - 7. [[Readout GUI (ReadoutShell)|c397]]
    - 7.1. [[Running and using the ReadoutShell|c397#AEN411]]
    - 7.2. [[Event file organization|x479]]
    - 7.3. [[Customizing Readout Shell|x513]]
  - 8. [[Epics Channel logging|c656]]
  - 9. [[Providing EPICS channel information to Tcl Servers|c669]]
  - 10. [[The epics display utility|c707]]
  - [[epicsdisplay
          NSCLRingDAQ
  10.0+
          Ron Fox|r726]] -- Display epics channels
  - 11. [[cratelocator|c806]]
  - 12. [[CAEN V812 Constant Fraction Discriminator|c819]]
  - 13. [[N568B CAENnet shaping amplifier|c856]]
  - 14. [[VHS-40xxx SBS support.|c891]]
  - 15. [[The tcl server application|c926]]
  - 16. [[Dumping events from ringbuffer or from file|c945]]
    - 16.1. [[Item dump formats and examples|c945#AEN973]]
  - 17. [[Compatibility utilities|c1009]]
    - 17.1. [[Format conversion with compatibilitybuffer|c1009#AEN1022]]
    - 17.2. [[Writing event files with compatibilitylogger|x1046]]
    - 17.3. [[Convenience scripts|x1065]]
    - 17.4. [[BufferToRing|x1100]]
  - 18. [[daqstart - Starting programs with logging and monitoring|c1105]]
  - 19. [[DvdBurner - Using Tcl to burn runs to DVD|c1128]]
  - 20. [[Utilities for burning data to DVD|c1153]]
  - 21. [[The Event log program|c1164]]
  - 22. [[The ringselector application|c1194]]
  - 23. [[Scaler Display Software.|c1269]]
  - 24. [[The Scaler Display Client|c1288]]
  - 25. [[Sequencing runs|c1299]]
    - 25.1. [[Configuring the sequencer.|c1299#AEN1304]]
    - 25.2. [[Using the sequencer.|x1369]]
- IV. [[libraries|p1389]]
  - 26. [[Integer byte order conversion library|c1391]]
    - 26.1. [[Using the conversion library in your code|c1391#AEN1398]]
    - 26.2. [[Byte order signatures and conversion blocks|x1415]]
    - 26.3. [[Data conversion|x1435]]
  - 27. [[Ring master class library.|c1472]]
  - 28. [[Networked ring buffer access|c1492]]
  - 29. [[Ring Buffer Primitives|c1553]]
    - 29.1. [[Incorporating ring buffer software|c1553#AEN1567]]
    - 29.2. [[Overview and Examples of ring buffers in action.|x1590]]
  - 30. [[The Tcl ring package|c1673]]
  - 31. [[The NSCL Exception class library|c1688]]
    - 31.1. [[Incorporating the library in your programs|c1688#AEN1709]]
    - 31.2. [[Exception classes|x1719]]
  - 32. [[Shared memory|c1749]]
    - 32.1. [[Overview of the API, and using it from within your C++ software|c1749#AEN1762]]
    - 32.2. [[Compiling/Linking your software with the shared memory API|x1820]]
  - 33. [[Access control and security|c1839]]
    - 33.1. [[Incorporting the software into your code|c1839#AEN1845]]
    - 33.2. [[Authenticators|x1859]]
    - 33.3. [[Interactors|x1904]]
  - 34. [[C++ encapsulation of a Tcl API subset|c1972]]
  - 35. [[NSCL DAQ Thread Library|c2030]]
    - 35.1. [[The thread and synchronization model|c2030#AEN2040]]
    - 35.2. [[Incorporating the library into an application.|x2131]]
    - 35.3. [[Pointers to the reference material|x2142]]
  - 36. [[Parsing and URIs|c2159]]
  - 37. [[Event builder client API|c2217]]
    - 37.1. [[C++ Client API|c2217#AEN2226]]
    - 37.2. [[Incorporating the event builder client library|x2240]]
    - 37.3. [[Connecting to the event builder.|x2264]]
    - 37.4. [[Disconnecting from the event builder.|x2297]]
    - 37.5. [[Sending data to the event builder.|x2315]]
    - 37.6. [[The Event orderer/event builder API|x2405]]
    - 37.7. [[Callbacks|x2439]]
  - 38. [[Format of Event Data In Ring Buffers|c2475]]
    - 38.1. [[The basic data formats|c2475#AEN2489]]
    - 38.2. [[Selecting Data From a Ring Buffer|x2716]]
    - 38.3. [[Incorporating the headers and libraries into your applications.|x2744]]
    - 38.4. [[Creating ring items|x2825]]
  - 39. [[S800 ReadoutCallouts|c2862]]
    - 39.1. [[S800 Data acquisition system|c2862#AEN2865]]
    - 39.2. [[Scope of the integration problem.|x2872]]
    - 39.3. [[Using the S800 integration package|x2888]]
  - 40. [[The NSCL Exception class library|c2929]]
    - 40.1. [[Incorporating the library in your programs|c2929#AEN2950]]
    - 40.2. [[Exception classes|x2960]]
  - 41. [[C++ encapsulation of a Tcl API subset|c2990]]
  - 42. [[The NSCL Exception class library|c3048]]
    - 42.1. [[Incorporating the library in your programs|c3048#AEN3069]]
    - 42.2. [[Exception classes|x3079]]
  - 43. [[C++ encapsulation of a Tcl API subset|c3109]]
  - 44. [[SBS Base interface classes to the VME|c3167]]
    - 44.1. [[The classes|c3167#AEN3181]]
    - 44.2. [[Incorporating headers and libraries into your program.|x3238]]
  - 45. [[Tcl CAENet package|c3251]]
  - 46. [[The CES CBD 8210 Tcl CAMAC Package|c3292]]
    - 46.1. [[Incorporating camac into your scripts|c3292#AEN3304]]
    - 46.2. [[An overview of the use of the camac package|x3323]]
  - 47. [[The Wienercamac Tcl package|c3342]]
    - 47.1. [[Incorporating wienercamac in your scripts.|c3342#AEN3356]]
    - 47.2. [[Using wienercamac|x3388]]
  - 48. [[SBS VME Module level device support software|c3530]]
- V. [[servers|p3542]]
  - 49. [[The RingMaster server|c3544]]
    - 49.1. [[The RingMaster Protocol|c3544#AEN3557]]
  - 50. [[Service Port Manager.|c3695]]
- VI. [[frameworks|p3711]]
  - 51. [[Event orderer and its user interface|c3713]]
    - 51.1. [[Event orderer design philosophy.|c3713#AEN3728]]
    - 51.2. [[Using the standard event orderer startup script|x3733]]
    - 51.3. [[Writing an event orderer startup script|x3744]]
    - 51.4. [[Event orderer packages|x3810]]
  - 52. [[Event builder client framework|c3879]]
    - 52.1. [[Application specific code for the event builder|c3879#AEN3899]]
    - 52.2. [[Building event builder clients.|x4067]]
    - 52.3. [[Running event builder clients|x4112]]
    - 52.4. [[ringFragmentSource - a prepackaged client for ringbuffer data sources|x4145]]
  - 53. [[Event builder Readout Callouts|c4231]]
    - 53.1. [[API layer|c4231#AEN4241]]
    - 53.2. [[EZBuilder|x4248]]
  - [[Preface|f4252]]
  - [[EVBC::start|r4255]] -- Start the event builder pipeline.
  - [[EVBC::stop|r4320]] -- Stop the event builder pipeline.
  - [[EVBC::reset|r4333]] -- Reset timestamp history
  - [[EVBC::flush|r4347]] -- Flush event builder event queues.
  - [[EVBC::startRingSource|r4360]] -- Start a ring fragment source for the event builder.
  - [[EVBC::startS800Source|r4406]] -- Start S800 data source
  - [[Preface|f4424]]
  - [[EVBC::initialize|r4430]] -- Initialize the EZBuilder layer.
  - [[EVBC::onBegin|r4483]] -- EZBuilder begin run actions
  - [[EVBC::onEnd|r4502]] -- EZBuilder end run actions.
  - [[Event builder client framework|r4516]] -- Event builder cilent framework
  - [[EVB::handleFragment|r4560]] -- Submit event fragments.
  - [[EVB::inputStats|r4579]] -- Event builder input statistics
  - [[EVB::outputStats|r4627]] -- Get orderer output statistics
  - [[EVB::dlatestats|r4646]] -- Get the late fragment statistics.
  - [[EVB::onDataLate|r4674]] -- Bind scripts to data late events.
  - [[EVB::barriertrace|r4698]] -- Supply a script to invoke on barrier events.
  - [[EVB::source|r4718]] -- Create event source queues.
  - [[EVB::deadsource|r4736]] -- Mark a data source dead.
  - [[EVB::reviveSocket|r4751]] -- Revive all dead data sources associated with a socket
  - [[EVB::flush|r4766]] -- Empty all input queues.
  - [[EVB::reset|r4779]] -- Reset timestamp clocks.
  - 54. [[The SBS Readout framework|c4792]]
    - 54.1. [[SBS Readout concepts|c4792#AEN4803]]
    - 54.2. [[Obtaining and building the skeleton application|x5095]]
    - 54.3. [[Modifying the skeleton application to meet your needs|x5110]]
    - 54.4. [[Readout commands|x5182]]
    - 54.5. [[Embedded Tcl server|x5198]]
    - 54.6. [[Running a readout application|x5208]]
  - 55. [[CCUSB Readout framework|c5213]]
    - 55.1. [[How the CCUSB readout framework works|c5213#AEN5237]]
    - 55.2. [[Writing DAQ configuration files|x5253]]
    - 55.3. [[Writing device support software|x5294]]
    - 55.4. [[Tcl device driver support|x5455]]
    - 55.5. [[The slow controls subsystem|x5713]]
    - 55.6. [[Running CCUSBReadout|x5726]]
  - 56. [[VMUSB readout|c5775]]
    - 56.1. [[How the VMUSB readout framework works|c5775#AEN5801]]
    - 56.2. [[Writing DAQ configuration files|x5817]]
    - 56.3. [[Writing C++ device support software|x5848]]
    - 56.4. [[Writing device support software in Tcl|x6022]]
    - 56.5. [[The slow controls subsystem|x6256]]
    - 56.6. [[Pushing external data into the event stream|x6297]]
    - 56.7. [[Running VMUSBReadout|x6339]]
- VII. [[Reference Pages|p6393]]
  - I. [[1compatibility|r6395]]
    - [[compatibilitybuffer|r6397]] -- Filter ring items to spectrodaq buffers
    - [[compatibilitylogger|r6435]] -- Create spectrodaq formatted event log files.
    - [[eventlog-compat|r6475]] -- Provide event logger pipeline for use with ReadoutGUI.
    - [[spectcldaq|r6522]] -- Pipe data source for SpecTcl in spectrodaq buffer mode.
    - [[spectcldaq.server|r6563]] -- TCP/IP server of ring data in spectrodaq format.
    - [[BufferToRing|r6624]] -- Convert old buffered data to ring buffer format.
  - II. [[1daq|r6643]]
    - [[ringbuffer|r6645]] -- Manage ring buffers.
    - [[ringtostdout|r6743]] -- Transmit data from a ring buffer to stdout.
    - [[stdintoring|r6797]] -- Pipe stdin to a ring buffer.
    - [[evttclsh|r6849]] -- Tcl interpreter that always runs an event loop
    - [[frag2ring|r6862]] -- Filter flattened fragments to ring items.
    - [[glom|r6940]] -- Glue event fragments together into events
    - [[S800 Ring fragment data source|r6979]] -- Event builder ring fragment source from s800
    - [[teering|r7051]] -- Tee data to stdout and a ringbuffer.
    - [[Readout Gui|r7076]] -- Encapsulate data sources in a graphical user interface
    - [[evttclsh|r7696]] -- Tcl interpreter that always runs an event loop
    - [[evttclsh|r7709]] -- Tcl interpreter that always runs an event loop
    - [[dumper|r7722]] -- Produce a formatted dump of event data.
    - [[daqstart|r7798]] -- Monitor essential programs
    - [[eventlog|r7873]] -- Record Event Data to Disk.
    - [[ringselector|r7934]] -- Provide selected ring data to non NSCL DAQ aware clients
    - [[sclclient|r8051]] -- Maintain scaler state in a tclserver
    - [[tkdumper|r8185]] -- GUI Dump of ring buffer items.
  - III. [[1epics|r8199]]
    - [[chanlog|r8201]] -- Write a set of channels to file
    - [[controlpush|r8257]] -- 
                Push epics data into a Tcl Server (e.g. production readout).
  - IV. [[1evb|r8356]]
    - [[EVB::BarrierStats::incomplete|r8358]] -- Display incomplete barrier statistics
    - [[EVB::BarrierStats::queueBarriers|r8448]] -- Displays per queue barrier statistics
    - [[EVB::BarrierStats::Summary|r8517]] -- UI element to summarize barrier statistics.
    - [[EVB::CallbackManager|r8549]] -- Object that manages callback sets.
    - [[EVB::connectionList|r8629]] -- List event builder connections
    - [[EVB::GUI procs|r8671]] -- Standard monitor UI procs.
    - [[EVB::inputStatistics::statusDisplay|r8716]] -- Widget to display input statitics
    - [[EVB::inputStatistics::queueStats|r8883]] -- Per queue input statistics widget
    - [[::EVB::inputStatistics::queueDisplay|r8976]] -- Display input queue statistics
    - [[EVB::inputStatistics::summaryDisplay|r9028]] -- Summary of input statistics.
    - [[EVB::lateFragments|r9080]] -- Late fragment statistics
    - [[EVB::lateSummary|r9151]] -- Widget to display summar of data late fragments.
    - [[::EVB::outputStatistics|r9186]] -- Complete output statistics widget
    - [[::EVB::outputSummary|r9273]] -- Summarize output statistics
    - [[::EVB::utility::sortedPair|r9329]] -- Key value pair widget
    - [[::EVB::utility::sortedWidget|r9424]] -- General key/widget sorted list
    - [[EventBuilder|r9551]] -- Event builder utility **proc**s
    - [[Observer|r9685]] -- Support the Observer pattern
    - [[EvbOrderer|r9784]] -- Event orderer compiled commands.
  - V. [[1tcl|r10013]]
    - [[TCL Ring package.|r10015]] -- Access Rings from tcl.
    - [[cratelocator|r10142]] -- locate specific SBS VME crate controllers.
    - [[cesbcnaf|r10168]] -- CAMAC operation via a CES CAMAC interface
    - [[wienerbcnaf|r10193]] -- CAMAC operation via a Wiener VC32/CC32 board set
    - [[bcnaf|r10218]] -- bcnaf via SBS VME CAMAC interfaces
    - [[canev812control|r10254]] -- GUI for controlling CAEN V812 CFD modules
    - [[loadcfd|r10274]] -- Load settings in to a CAEN V812 CFD module.
    - [[loadshaper|r10293]] -- Load setttings into an N568 shaper via SBS/V288.
    - [[n568Control|r10311]] -- GUI for the n568 shaper.
    - [[vhqControl|r10334]] -- Control panel application for VHQ bias supply modules.
    - [[vhsPanel|r10350]] -- Canned VHS Control panel
    - [[SBS Vme Tcl package|r10378]] -- Provide access to VME crates to Tcl scripts.
    - [[DaqPortManager|r10485]] -- Manage TCP/IP service ports and advertise their allocations
    - [[tclserver|r10588]] -- Start a Tcl Server.
    - [[serverauth|r10631]] -- Control tcl server authorization.
    - [[dvdburn|r10677]] -- Command line tool to burn NSCLDAQ data DVDs.
    - [[burngui|r10704]] -- Graphical front end to dvdburn
    - [[ScalerDisplay|r10722]] -- Live Scaler Displays
  - VI. [[1sbsReadout|r10940]]
    - [[Readout|r10942]] -- Start an event readout program.
  - VII. [[3daq|r10982]]
    - [[CopyrightNotice|r10984]] -- Generate license/author credits.
    - [[cvt|r11080]] -- Integer byte order conversions
    - [[CRingMaster|r11266]] -- RingMaster access.
    - [[CRingAccess|r11458]] -- Remote Ring Access
    - [[CRingBuffer|r11644]] -- Low level ring buffer primitives
    - [[CException|r12452]] -- Abstract base class for the exception class hierarchy.
    - [[CErrnoException|r12539]] -- Exceptions that wrap the Unix `errno`
    - [[CRangeError|r12616]] -- Reports and exception for a value out of allowed range.
    - [[CStateException|r12754]] -- Exception for invalid state transitions.
    - [[CStreamIOError|r12853]] -- I/O error on a C++ stream.
    - [[CURIFormatException|r13016]] -- Report errors in universal resource identifiers (uri)s.
    - [[CMonitorException|r13201]] -- Exceptions for synchronization class abuse.
    - [[CInvalidArgumentException|r13336]] -- Report invalid function arguments.
    - [[CDAQShm|r13470]] -- class description
    - [[CAuthenticator|r13796]] -- Abstract base authenticator class.
    - [[CPasswordCheck|r13900]] -- Authenticate against a stored password.
    - [[CUnixUserCheck|r14088]] -- Authenticate against a unix user name and password.
    - [[CTclAccessListCheck|r14299]] -- Authenticate against a Tcl List.
    - [[CAccessListCheck|r14397]] -- Authenticate against a list of allowed credentials.
    - [[CHostListCheck|r14539]] -- Authenticate from a list of TCP/IP hosts
    - [[CInteractor|r14719]] -- Base class for security interactions.
    - [[CStringInteractor|r14888]] -- Provide an interactor that processes strings.
    - [[CFdInteractor|r15049]] -- Interact with  file descriptor
    - [[CIOInteractor|r15175]] -- Separate prompt and input interactors.
    - [[CTCLApplication 3|r15300]] -- 
                Base class for TCL/Tk applications.
    - [[CTCLException|r15343]] -- 
                Class for reporting exceptional conditions in Tcl applications
                via the C++ try/catch mechanism.
    - [[CTCLInterpreter|r15486]] -- 
                Encapsulate a Tcl interpreter.
    - [[CTCLInterpreterObject  3|r15704]] -- 
                Base class for objects that are associated with a Tcl Interpreter.
    - [[CTCLList|r15783]] -- 
                Provide access to Tcl List parsing.
    - [[CTCLObject|r15892]] -- 
                Encapsulate Tcl Dual ported objects.
    - [[CTCLObjectProcessor|r16123]] -- 
                Abstract base class to encapsulate the Tcl object command interface exposed by
                `Tcl_CreateObjCommand`.
    - [[CTCLVariable|r16216]] -- 
                Encapsulate Tcl interpreter variables.
    - [[CTCLProcessor|r16411]] -- 
                Provide `argc`, `argv`
                extension commands to Tcl.
    - [[CTCLChannel|r16600]] -- 
                Provide a C++ abstraction wrapper for Tcl Channels.
    - [[CTCLCommandPackage|r16770]] -- 
                Group several related Tcl command extensions and common services they
                may require together.
    - [[CTCLCompatibiltyProcessor|r16875]] -- 
                Adaptor between `CTCLOjbectProcessor`
                and `CTCLProcessor`.
    - [[CTCLFileHandler|r16942]] -- 
                Base class for building object oriented Tcl File event handlers.
    - [[CTCLHashTable|r17028]] -- 
                Object oriented interface to Tcl's hash table functions.
    - [[CTCLHashTableItem|r17159]] -- 
                Encapsulation of an entry in a Tcl Hash table as encapsulated
                in `CTCLHashTable`
    - [[CTCLHashTableIterator|r17227]] -- 
                Iterator for visiting all elements of a `CTCLHashTable`
    - [[CTCLIdleProcess|r17323]] -- 
                Allows the establishment of an executable object that
                can be scheduled to be invoked when the Tcl/Tk intperpreter
                has no events that require processing.
    - [[CTCLPackagedCommand|r17384]] -- 
                Base class for a command that lives in a `CTCLCommandPackage`
    - [[CTCLResult|r17445]] -- 
                Provide an object oriented interace to the Tcl interpreter result.
    - [[CTCLString|r17556]] -- 
                Provide a wrapper for the Tcl_DString data type
                and its API
    - [[CTCLTimer|r17773]] -- 
                Abstract base class for C++ objects attached to timer events.
    - [[CTCLLiveEventLoop|r17843]] -- Run Tcl with event loop.
    - [[CTCLChannelCommander|r17947]] -- Accept commands on a Tcl channel from the event loop.
    - [[CTCLStdioCommander|r18159]] -- Event driven command input on stdin/stdout
    - [[CTCLServer|r18223]] -- Listener for a Tcl server.
    - [[CTCLTcpServerInstance|r18351]] -- Channel commander that is a server instance for `CTCLServer`
    - [[CTCLObjectPackage|r18424]] -- Provide common functionality for a set of
                    related commands.
    - [[CTCLPackagedObjectProcessor|r18486]] -- Base class for commands living in a
                        `CTCLObjectPackage`
    - [[CItemConfiguration|r18586]] -- Hold a configuration
    - [[CConfigurableObject|r19309]] -- Base class for objects tht have a configuration.
    - [[Thread|r19529]] -- Abstract base class for thread objects.
    - [[Synchronizable|r19663]] -- Wait queue for threads
    - [[SyncGuard|r19761]] -- Provide Critical Regions, Monitors
    - [[URL|r19928]] -- Parse Uniform Resource Identifiers (URI)
    - [[CEvbClientApp|r20076]] -- Framework event builder client application.
    - [[CEVBClientFramework|r20220]] -- Event builder client framework.
    - [[CEventOrderClient|r20276]] -- Client of the event orderer
    - [[CRingItem|r20487]] -- Encapsulates an item in a ring buffer.
    - [[CRingScalerItem|r20784]] -- Encapsulate ring buffer scaler items.
    - [[CRingStateChangeItem|r21133]] -- Encapsulate a ring buffer state change item.
    - [[CRingTextItem|r21444]] -- Encapsulate ring items that are lists of text strings.
    - [[CRingPhysicsEventCountItem|r21671]] -- Provides statistics regarding the number of events produced.
    - [[CRingFragmentItem|r21906]] -- Encapsulate a EVB_FRAGMENT ring item
    - [[CRingSelectionPredicate|r22179]] -- Base class for predicates that select items from
                ring buffers.
    - [[CAllButPredicate|r22510]] -- Select all ring items except some.
    - [[CDesiredTypesPredicate|r22685]] -- Only accept specified ring item types.
    - [[DataFormat.h|r22849]] -- Format of ring items.
    - [[format  Functions|r23303]] -- Functions to create ring items.
    - [[CDataSource|r23559]] -- Abstract base class of data source for ring items.
    - [[CRingDataSource|r23600]] -- Ringbuffer data source for ring items.
    - [[CFileDataSource|r23668]] -- Ring item data source from a file
    - [[CDataSourceFactory"|r23725]] -- Create data sources given a URI
    - [[CRingItemFactory|r23781]] -- Upcast ring items to specific ring item objects.
    - [[CException|r23873]] -- Abstract base class for the exception class hierarchy.
    - [[CErrnoException|r23960]] -- Exceptions that wrap the Unix `errno`
    - [[CRangeError|r24037]] -- Reports and exception for a value out of allowed range.
    - [[CStateException|r24175]] -- Exception for invalid state transitions.
    - [[CStreamIOError|r24274]] -- I/O error on a C++ stream.
    - [[CURIFormatException|r24437]] -- Report errors in universal resource identifiers (uri)s.
    - [[CMonitorException|r24622]] -- Exceptions for synchronization class abuse.
    - [[CInvalidArgumentException|r24757]] -- Report invalid function arguments.
    - [[CTCLApplication 3|r24891]] -- 
                Base class for TCL/Tk applications.
    - [[CTCLException|r24934]] -- 
                Class for reporting exceptional conditions in Tcl applications
                via the C++ try/catch mechanism.
    - [[CTCLInterpreter|r25077]] -- 
                Encapsulate a Tcl interpreter.
    - [[CTCLInterpreterObject  3|r25295]] -- 
                Base class for objects that are associated with a Tcl Interpreter.
    - [[CTCLList|r25374]] -- 
                Provide access to Tcl List parsing.
    - [[CTCLObject|r25483]] -- 
                Encapsulate Tcl Dual ported objects.
    - [[CTCLObjectProcessor|r25714]] -- 
                Abstract base class to encapsulate the Tcl object command interface exposed by
                `Tcl_CreateObjCommand`.
    - [[CTCLVariable|r25807]] -- 
                Encapsulate Tcl interpreter variables.
    - [[CTCLProcessor|r26002]] -- 
                Provide `argc`, `argv`
                extension commands to Tcl.
    - [[CTCLChannel|r26191]] -- 
                Provide a C++ abstraction wrapper for Tcl Channels.
    - [[CTCLCommandPackage|r26361]] -- 
                Group several related Tcl command extensions and common services they
                may require together.
    - [[CTCLCompatibiltyProcessor|r26466]] -- 
                Adaptor between `CTCLOjbectProcessor`
                and `CTCLProcessor`.
    - [[CTCLFileHandler|r26533]] -- 
                Base class for building object oriented Tcl File event handlers.
    - [[CTCLHashTable|r26619]] -- 
                Object oriented interface to Tcl's hash table functions.
    - [[CTCLHashTableItem|r26750]] -- 
                Encapsulation of an entry in a Tcl Hash table as encapsulated
                in `CTCLHashTable`
    - [[CTCLHashTableIterator|r26818]] -- 
                Iterator for visiting all elements of a `CTCLHashTable`
    - [[CTCLIdleProcess|r26914]] -- 
                Allows the establishment of an executable object that
                can be scheduled to be invoked when the Tcl/Tk intperpreter
                has no events that require processing.
    - [[CTCLPackagedCommand|r26975]] -- 
                Base class for a command that lives in a `CTCLCommandPackage`
    - [[CTCLResult|r27036]] -- 
                Provide an object oriented interace to the Tcl interpreter result.
    - [[CTCLString|r27147]] -- 
                Provide a wrapper for the Tcl_DString data type
                and its API
    - [[CTCLTimer|r27364]] -- 
                Abstract base class for C++ objects attached to timer events.
    - [[CTCLLiveEventLoop|r27434]] -- Run Tcl with event loop.
    - [[CTCLChannelCommander|r27538]] -- Accept commands on a Tcl channel from the event loop.
    - [[CTCLStdioCommander|r27750]] -- Event driven command input on stdin/stdout
    - [[CTCLServer|r27814]] -- Listener for a Tcl server.
    - [[CTCLTcpServerInstance|r27942]] -- Channel commander that is a server instance for `CTCLServer`
    - [[CTCLObjectPackage|r28015]] -- Provide common functionality for a set of
                    related commands.
    - [[CTCLPackagedObjectProcessor|r28077]] -- Base class for commands living in a
                        `CTCLObjectPackage`
    - [[CItemConfiguration|r28177]] -- Hold a configuration
    - [[CConfigurableObject|r28900]] -- Base class for objects tht have a configuration.
    - [[CException|r29120]] -- Abstract base class for the exception class hierarchy.
    - [[CErrnoException|r29207]] -- Exceptions that wrap the Unix `errno`
    - [[CRangeError|r29284]] -- Reports and exception for a value out of allowed range.
    - [[CStateException|r29422]] -- Exception for invalid state transitions.
    - [[CStreamIOError|r29521]] -- I/O error on a C++ stream.
    - [[CURIFormatException|r29684]] -- Report errors in universal resource identifiers (uri)s.
    - [[CMonitorException|r29869]] -- Exceptions for synchronization class abuse.
    - [[CInvalidArgumentException|r30004]] -- Report invalid function arguments.
    - [[CTCLApplication 3|r30138]] -- 
                Base class for TCL/Tk applications.
    - [[CTCLException|r30181]] -- 
                Class for reporting exceptional conditions in Tcl applications
                via the C++ try/catch mechanism.
    - [[CTCLInterpreter|r30324]] -- 
                Encapsulate a Tcl interpreter.
    - [[CTCLInterpreterObject  3|r30542]] -- 
                Base class for objects that are associated with a Tcl Interpreter.
    - [[CTCLList|r30621]] -- 
                Provide access to Tcl List parsing.
    - [[CTCLObject|r30730]] -- 
                Encapsulate Tcl Dual ported objects.
    - [[CTCLObjectProcessor|r30961]] -- 
                Abstract base class to encapsulate the Tcl object command interface exposed by
                `Tcl_CreateObjCommand`.
    - [[CTCLVariable|r31054]] -- 
                Encapsulate Tcl interpreter variables.
    - [[CTCLProcessor|r31249]] -- 
                Provide `argc`, `argv`
                extension commands to Tcl.
    - [[CTCLChannel|r31438]] -- 
                Provide a C++ abstraction wrapper for Tcl Channels.
    - [[CTCLCommandPackage|r31608]] -- 
                Group several related Tcl command extensions and common services they
                may require together.
    - [[CTCLCompatibiltyProcessor|r31713]] -- 
                Adaptor between `CTCLOjbectProcessor`
                and `CTCLProcessor`.
    - [[CTCLFileHandler|r31780]] -- 
                Base class for building object oriented Tcl File event handlers.
    - [[CTCLHashTable|r31866]] -- 
                Object oriented interface to Tcl's hash table functions.
    - [[CTCLHashTableItem|r31997]] -- 
                Encapsulation of an entry in a Tcl Hash table as encapsulated
                in `CTCLHashTable`
    - [[CTCLHashTableIterator|r32065]] -- 
                Iterator for visiting all elements of a `CTCLHashTable`
    - [[CTCLIdleProcess|r32161]] -- 
                Allows the establishment of an executable object that
                can be scheduled to be invoked when the Tcl/Tk intperpreter
                has no events that require processing.
    - [[CTCLPackagedCommand|r32222]] -- 
                Base class for a command that lives in a `CTCLCommandPackage`
    - [[CTCLResult|r32283]] -- 
                Provide an object oriented interace to the Tcl interpreter result.
    - [[CTCLString|r32394]] -- 
                Provide a wrapper for the Tcl_DString data type
                and its API
    - [[CTCLTimer|r32611]] -- 
                Abstract base class for C++ objects attached to timer events.
    - [[CTCLLiveEventLoop|r32681]] -- Run Tcl with event loop.
    - [[CTCLChannelCommander|r32785]] -- Accept commands on a Tcl channel from the event loop.
    - [[CTCLStdioCommander|r32997]] -- Event driven command input on stdin/stdout
    - [[CTCLServer|r33061]] -- Listener for a Tcl server.
    - [[CTCLTcpServerInstance|r33189]] -- Channel commander that is a server instance for `CTCLServer`
    - [[CTCLObjectPackage|r33262]] -- Provide common functionality for a set of
                    related commands.
    - [[CTCLPackagedObjectProcessor|r33324]] -- Base class for commands living in a
                        `CTCLObjectPackage`
    - [[CItemConfiguration|r33424]] -- Hold a configuration
    - [[CConfigurableObject|r34147]] -- Base class for objects tht have a configuration.
    - [[CVMEInterface|r34367]] -- Class wrapping of the SBS VME library.
    - [[CSBSBit3VmeInterface|r34682]] -- Provide access to SBS/Bit3 driver parameters.
    - [[CVME<T>|r35231]] -- Reference counted pointer like object to VME address segments.
    - [[CVMEModule|r35632]] -- Provide a base set of services for a VME module driver class.
    - [[CMmapError|r35957]] -- Report errors in memory mapping requests.
    - [[CADC2530|r36013]] -- Support the Hytec NADC 2530 Peak sensing ADC.
    - [[CAENcard|r36475]] -- Support for the CAEN 32 bit digitizers
    - [[CBD8210|r37270]] -- CES CBD 8210 CAMAC branch highway driver (obsolete)
    - [[CCAENV1x90|r37638]] -- Support for the CAEN V1190 and V1290
                        multihit, complicated TDC.
    - [[CCAENV560|r40020]] -- Support the CCAENV560 non-latching scaler.
    - [[CCAENV830|r40184]] -- Support driver for the CAEN V820/V830 latching scaler module.
    - [[CCAENV977|r40741]] -- Software support for the CAEN V977 I/O register.
    - [[CCAMACScalerLRS2551|r41140]] -- Support software for the LeCroy LRS 2551 12 channel CAMAC scaler
    - [[CCAMACScalerLRS4434|r41250]] -- High level support software for the 32 channel LeCroy LRS 4434 CAMAC scaler module
    - [[CCAMACStatusModule|r41362]] -- Provide computer busy status support for the BiRA CAMAC
                    NIM out module.
    - [[CCAMACTrigger|r41470]] -- Trigger module for the CES CBD 8210 VME CAMAC Parallel Branch Highway Driver
    - [[CCamac|r41524]] -- Manages CAMAC memory maps.
    - [[CCamacModule|r41606]] -- Provide support for a generic CAMAC module.
    - [[CCamacNimout|r41980]] -- Provides low level support for the BiRa CAMAC Nim output module.
    - [[CCrateController|r42069]] -- Encapsulation of a BiRa 1302 CAMAC controller via CES CBS8210.
    - [[CSIS3600|r42409]] -- Support for the SIS 3600 VME latch module.
    - [[CSIS3820|r42868]] -- Low level support for SIS 3820 32 channel latching scaler module
    - [[CScaler|r43574]] -- Abstract base class for reading scalers into a vector
    - [[CStatusModule|r43681]] -- Abstract base class for status modules.
    - [[CTrigger|r43746]] -- Abstract base class for triggers
    - [[CVME|r43774]] -- Pointer like object for accessing the VME
    - [[CVMEScalerLRS1151|r44118]] -- High level support for the LeCroy LRS 1151 VME scaler.
    - [[CVMEStatusModule|r44205]] -- Implement a status module using the CAEN V262 module.
    - [[CVMETrigger|r44289]] -- VME trigger class based on the CAEN V262 I/O module.
    - [[CVMEptr|r44340]] --
    - [[CaenIO|r44683]] -- Support for the CAEN V262 I/O register module.
    - [[CMmapError|r44830]] -- Exception that can be thrown in the event of memory mapping errors.
    - [[CNimout|r44865]] -- Low level support for the BiRa VME nim output module
    - [[CVmeModule|r45139]] -- Convenience base class for implementing VME module support
    - [[CSIS3300|r45437]] -- Low Level support for the SIS 3300 Flash ADC module
    - [[CPortManager|r46170]] -- Provide a C++ interface to the server port manager daemon.
    - [[CPortManagerException|r46317]] -- Report errors conditions in port manager transactions
  - VIII. [[3ccusb|r46463]]
    - [[addtcldriver|r46465]] -- Register Tcl command ensemble as a device module
    - [[ad811|r46491]] -- Support the Ortec AD811 ADC
    - [[c1205|r46547]] -- Manage CAEN C1205 QDC modules.
    - [[c257|r46667]] -- Manages the C257 scaler module
    - [[ccusb (command)|r46740]] -- Configure and read scalers from CC-USB module
    - [[lrs2228|r46940]] -- Manages the LRS2228 TDC
    - [[lrs2249|r46997]] -- Manage LeCroy 2249 QDC modules
    - [[lrs2551|r47050]] -- Manage LRS 2551 modules
    - [[ph7xxx|r47126]] -- Define Phillips ADC/TDC/QDC modules
    - [[stack|r47320]] -- Create and configure CC-USB stacks.
    - [[Module|r47448]] -- Create and manipulate slow control device instances
    - [[Slow controls protocol|r47490]] -- TCP/IP slow control protocol
    - [[CCCUSB|r47601]] -- Provide access to a CC-USB device.
    - [[CCCUSBReadoutList|r50336]] -- Create lists of CAMAC commands for CC-USB controllers.
    - [[CConfigurableObject|r50799]] -- base class for devices that have a configuration
    - [[cccusb|r52051]] -- Swig wrapping of the CCCUSB C++ class.
    - [[cccusbreadoutlist|r52779]] -- Tcl wrapping of `CCCUSBReadoutList`
  - IX. [[3vmusb|r53046]]
    - [[adc|r53048]] -- Create/configure CAEN V775, V785, V792, V862 modules.
    - [[caenchain|r53182]] -- Aggregate adc modules into CBLT readout chains.
    - [[vmusb|r53231]] -- Control VM-USB resources and read internal scalers
    - [[sis330x|r53428]] -- Driver for SIS3300/1 FADC
    - [[sis3820|r53592]] -- Create and configure SIS 3820 scaler modules
    - [[v830|r53638]] -- Create and configure CAEN V830 32 channel scalers.
    - [[v977|r53817]] -- Create and configure CAEN V977 Input registers
    - [[sis3804|r53929]] -- Create and configure SIS 3804 scalers
    - [[hinp|r53988]] -- XLM-XXV with Wash-U HINP firmware.
    - [[psd|r54047]] -- XLM with Wash-U pulse shape discrmination firmware
    - [[hira|r54082]] -- Pair up to 2 XLMs and FADC for HiRA
    - [[hytec|r54134]] -- Support the Hytec NADC 2530 adc module.
    - [[tcl driver support|r54289]] -- tcl driver support functions.
    - [[madc|r54426]] -- Acquire events from Mesytec MADC32 ADC.
    - [[madcchain|r54677]] -- Support CBLT chains of MADC32 modules.
    - [[madcscaler|r54738]] -- Support dead-time counters in MADC32 as scalers.
    - [[mase|r54775]] -- Support for XLM with MASE firmware.
    - [[tdc1x90|r54825]] -- Provide support for the CAEN V1x90 TDC family.
    - [[v1729a|r55080]] -- CAENV1729a waveform digitizer.
    - [[stack|r55210]] -- Compose and configure VM-USB readout stacks.
    - [[CVMUSB|r55338]] -- Interface with VM-USB controller.
    - [[CVMUSBReadoutList|r57342]] -- Construct VM-USB stacks
    - [[CVMUSBRemote|r58237]] -- Execute lists remotely on VMUSBReadout
    - [[CConfigurableObject|r59464]] -- Configuration database
    - [[cvmusb|r60631]] -- SWIG Tcl wrapping of `CVMUSB`
    - [[cvmusbreadoutlist|r61379]] -- SWIG wrappers for `CVMUSBReadoutList`
    - [[Module|r61869]] -- control config command: create/configure modules.
    - [[watch|r62123]] -- Watch variables (slow controls)
    - [[VMUSB slow controls protocol|r62142]] -- VMUSB Slow controls protocol
  - X. [[3tcl|r62204]]
    - [[s800|r62206]] -- s800 Readout Callouts module
    - [[caennet|r62291]] -- Access CAENnet from Tcl scripts.
    - [[camac|r62356]] -- Provide access to CES CBD8210 CAMAC to Tcl scripts
    - [[wienercamac|r62523]] -- Tcl Script CAMAC access via VC32/CC32 boardset.
    - [[CFD812|r62661]] -- low level control of the CAEN V812 CFD
    - [[caenv812gui|r62801]] -- Megawidget control panel for the CAEN V812 CFD
    - [[n568b|r62933]] -- Support package for the CAEN N568B shaper.
    - [[n568Panel|r63121]] -- Control panel megawidget for N568 shaping amplifier
    - [[vhq|r63258]] -- Low level Tcl access to iSEG VHQ2xxx units.
    - [[vhqPanel|r63445]] -- Control widget for iSeg vhq2xx VME bias supply.
    - [[iSegVhs|r63638]] -- SBS support for VHS 404 modules.
    - [[VhsWidgets|r64142]] -- User interface components for VHS 404 power supplies.
    - [[portAllocator|r64221]] -- Tcl API for the DaqPortManager daemon.
    - [[DvdBurner|r64299]] -- Burn NSCL Data to DVD
    - [[sequencer|r64351]] -- 
                Provide a ReadoutGui plugin for nscldaq 8.1 and later that can
                automate several data taking runs.
  - XI. [[3sbsReadout|r64477]]
    - [[CBusy|r64479]] -- Abstract base class for Busy module management.
    - [[CCAENV262Busy|r64534]] -- Concrete busy class for the CAEN V262 input module.
    - [[CCAENV262Triger|r64659]] -- Trigger module with CAEN V262
    - [[CCompoundEventSegment|r64763]] -- Container for other event segments
    - [[CDocumentedPacket|r64985]] -- Encapsulate event data in a packet that is documented.
    - [[CEventPacket|r65248]] -- Encapsulate an event segment in a documented packet.
    - [[CEventSegment|r65366]] -- Base class for all event segments.
    - [[CEventTrigger|r65545]] -- Abstract base class for triggers.
    - [[CExperiment|r65600]] -- Encapsulate the experiment.
    - [[CInvalidPacketStateException|r65873]] -- Exception thrown by documented packets.
    - [[CNullTrigger|r65983]] -- A trigger that never fires.
    - [[CReadoutException|r66003]] -- Base class for readout specific exceptions
    - [[CScalerBank|r66027]] -- Container for individual Scaler objects.
    - [[CTimedTrigger|r66269]] -- CEventTrigger that fires periodically
    - [[CV977Busy|r66357]] -- Concrete busy class using the CAEN V977 module
    - [[CV977Trigger|r66459]] -- Concrete Trigger class using CAEN V977 module.
    - [[RunState|r66553]] -- Encapsulate important state of the software.
    - [[CScaler|r66653]] -- Base class for scaler readout classes
  - XII. [[5daq|r66739]]
    - [[eventorderer|r66741]] -- Event orderer protocol
  - XIII. [[5tcl|r66856]]
    - [[caen812configfile|r66858]] -- Format of configuration files for CAENV 812 software.
    - [[n568configfile|r66964]] -- N568 shaper configuration file
    - [[vhqconfig|r67080]] --  Config file for

- **List of Tables**
- 7-1. [[Data Acquisition configuration parameters|x513#AEN575]]
- 7-2. [[Directory root configuration parameters|x513#AEN596]]
- 7-3. [[State Parameters|x513#AEN616]]
- 47-1. [[Wiener CC32 addressing convention|x3388#AEN3392]]

- **List of Figures**
- 7-1. [[Readout GUI Directory tree|x479#AEN495]]

- **List of Examples**
- 2-1. [[Adding **ringbuffer**'s directory to bash's search path:|c265#AEN278]]
- 2-2. [[Adding command paths to csh|c265#AEN284]]
- 5-1. [[Appending the NSCLDAQ Tcl Package repository to Tcl's search
            path|c342#AEN366]]
- 5-2. [[Appending NSLCDAQ's TclPackage repository to Tcl's search path|c342#AEN370]]
- 5-3. [[Requesting the VME Tcl package be loaded.|c342#AEN374]]
- 5-4. [[Using VME Tcl to locate all 2530 modules|x377#AEN381]]
- 7-1. [[ReadoutCallouts.tcl sample extension|x513#AEN561]]
- 15-1. [[Using **serverauth** to authorize a node|c926#AEN941]]
- 16-1. [[Dumping data from the ring buffer named 0400x on spdaq22|c945#AEN959]]
- 16-2. [[Dumping data from the event file segment
            /user/0400x/complete/run-1234-00.evt|c945#AEN963]]
- 16-3. [[State Transition items|c945#AEN976]]
- 16-4. [[Text List items|c945#AEN981]]
- 16-5. [[Incremental Scalers dump|c945#AEN986]]
- 16-6. [[Event count items|c945#AEN992]]
- 16-7. [[Physics Event items|c945#AEN998]]
- 16-8. [[Unknown item types|c945#AEN1003]]
- 17-1. [[Converting a ring buffer event file with compatibilitybuffer|c1009#compatibilitybuffer-ex1]]
- 17-2. [[Converting ring buffer data to a 8Kword (16Kbyte) old style event file|c1009#AEN1030]]
- 17-3. [[Using compatibilitylogger to convert event files|x1046#AEN1060]]
- 17-4. [[Attaching SpecTcl to ring buffers in compatibility mode|x1065#AEN1080]]
- 18-1. [[Logging errors and informing on exit|c1105#AEN1122]]
- 19-1. [[Requesting the DvdBurner package|c1128#AEN1137]]
- 19-2. [[Writing runs to DVD using DvdBurner|c1128#AEN1143]]
- 19-3. [[Writing all runs to DVD|c1128#AEN1149]]
- 21-1. [[Taking data from a remote ring|c1164#AEN1189]]
- 22-1. [[Dumping state changes and sampled event data with od|c1194#AEN1247]]
- 22-2. [[Dumping all but packet types|c1194#AEN1255]]
- 22-3. [[Attaching SpecTcl|c1194#AEN1263]]
- 25-1. [[Loading the sequencer package|c1299#AEN1349]]
- 26-1. [[Including the cvt header|c1391#AEN1401]]
- 26-2. [[Compiling a C or C++ source file that includes cvt.h|c1391#AEN1407]]
- 26-3. [[A makefile rule that builds a C++ program using the
                cvt package|c1391#AEN1411]]
- 26-4. [[Creating a DaqConversion|x1415#AEN1428]]
- 27-1. [[Including the header|c1472#AEN1481]]
- 27-2. [[Compiling code|c1472#AEN1484]]
- 27-3. [[Linking code to the library|c1472#AEN1487]]
- 28-1. [[A sample ring specification in URI form|c1492#AEN1500]]
- 28-2. [[Substituting local host for the hostname in URI's|c1492#AEN1508]]
- 28-3. [[Including the header|c1492#AEN1540]]
- 28-4. [[Compiling code that uses `CRingAccess`|c1492#AEN1543]]
- 28-5. [[Linking code that uses `CRingAccess`|c1492#AEN1547]]
- 29-1. [[Compilation line for ring buffer primitives|c1553#AEN1574]]
- 29-2. [[Including the ring buffer primitives header|c1553#AEN1580]]
- 29-3. [[Linking to the ring buffer primitives|c1553#AEN1586]]
- 29-4. [[Sample ring buffer consumer|x1590#AEN1604]]
- 29-5. [[A sample Ring Buffer producer program|x1590#AEN1653]]
- 30-1. [[Incorporating the ring package in your scripts|c1673#AEN1680]]
- 31-1. [[Catching `CException` and exiting|x1719#AEN1744]]
- 32-1. [[Shared memory library example|c1749#AEN1790]]
- 32-2. [[Compiling a C++ source that includes daqshm.h|x1820#AEN1831]]
- 32-3. [[Linking C++ object files that use the
            daqshm library|x1820#AEN1835]]
- 33-1. [[Compilation switches for the security includes|c1839#AEN1852]]
- 33-2. [[Link switches for the security library|c1839#AEN1856]]
- 33-3. [[Boilerplate DAQ Authorization code|x1859#AEN1863]]
- 35-1. [[The life of a thread|c2030#AEN2053]]
- 35-2. [[Why synchonization is needed|c2030#AEN2085]]
- 35-3. [[Using `SyncGuard` to implement a monitor|c2030#AEN2109]]
- 35-4. [[Compiling and linking NSCLDAQ threaded software|x2131#AEN2139]]
- 36-1. [[Sample URI library program|c2159#AEN2187]]
- 36-2. [[Building urltst.cpp|c2159#AEN2213]]
- 37-1. [[Connecting to the event builder as a data source.|x2264#AEN2267]]
- 37-2. [[Closing an event builder connection|x2297#AEN2312]]
- 37-3. [[Starting the event builder|x2405#AEN2416]]
- 37-4. [[Establishing the connection callback|x2439#AEN2447]]
- 37-5. [[Setting up the disconnect callback|x2439#AEN2464]]
- 38-1. [[Including a ring item class|x2744#AEN2750]]
- 38-2. [[Telling the compiler where to find Ring Item headers|x2744#AEN2757]]
- 38-3. [[Linking the ring item format libraries|x2744#AEN2762]]
- 39-1. [[A ReadoutCallouts.tcl for the s800|x2888#AEN2905]]
- 40-1. [[Catching `CException` and exiting|x2960#AEN2985]]
- 42-1. [[Catching `CException` and exiting|x3079#AEN3104]]
- 47-1. [[Enabling a module Lam with wienercamac|x3388#AEN3526]]
- 49-1. [[The CONNECT message format|c3544#AEN3579]]
- 49-2. [[Format of the DISCONNECT message|c3544#AEN3594]]
- 49-3. [[Format of the LIST command|c3544#AEN3608]]
- 49-4. [[Format of the REGISTER command|c3544#AEN3660]]
- 49-5. [[Format of the UNREGISTER message|c3544#AEN3670]]
- 49-6. [[Format of the REMOTE message|c3544#AEN3681]]
- 51-1. [[The standard startup script explained|x3744#AEN3749]]
- 52-1. [[`CEVBClientApp` definition|c3879#AEN3925]]
- 52-2. [[The `CEVBRingClientApp` class
                definition.|c3879#AEN3957]]
- 52-3. [[The `CEVBRingClientApp` `initialize`
                and `shutdown` methods.|c3879#AEN3971]]
- 52-4. [[The `CEVBRingClientApp`
`dataReady` method.|c3879#AEN3984]]
- 52-5. [[The `EVBRingClientApp` `getEvents`
                implementation.|c3879#AEN4028]]
- 52-6. [[Configuring the event builder client framework|x4067#AEN4078]]
- 52-7. [[S800 timestamp extractor (s800timestamp.c|x4145#AEN4184]]
- 54-1. [[Obtaining the SBS readout skeleton|x5095#AEN5100]]
- 55-1. [[Creating and configuring devices|x5253#AEN5257]]
- 55-2. [[Configuring an event stack|x5253#AEN5280]]
- 55-3. [[Setting up a scaler stack|x5253#AEN5291]]
- 55-4. [[Obtaining the ccusb driver development kit|x5294#AEN5299]]
- 55-5. [[Using a user written CCUSB driver|x5294#AEN5305]]
- 55-6. [[A snit CCUSB device driver module|x5455#AEN5502]]
- 55-7. [[CCUSB device support example writtin in Incr Tcl|x5455#AEN5599]]
- 55-8. [[DAQ config script fragment with tcl drivers.|x5455#AEN5710]]
- 56-1. [[Creating and configuring devices|x5817#AEN5821]]
- 56-2. [[Configuring an event stack|x5817#AEN5833]]
- 56-3. [[Configuring a VM-USB scaler stack|x5817#AEN5842]]
- 56-4. [[Obtaning the VM-USB device driver development kit|x5848#AEN5856]]
- 56-5. [[Using a user written VMUSB driver|x5848#AEN5865]]
- 56-6. [[The template driver `Initialize` method|x5848#AEN5927]]
- 56-7. [[Template Driver `addReadoutList` method|x5848#AEN5946]]
- 56-8. [[The VMUSB driver `Xxxx_Init`
                    function.|x5848#AEN5972]]
- 56-9. [[Itcl VM-USB device driver|x6022#AEN6045]]
- 56-10. [[A Snit VM-USB driver.|x6022#AEN6137]]
- 56-11. [[USing a Tcl VM-USB driver.|x6022#AEN6242]]
- 56-12. [[Specifying VM-USB monitored variables|x6297#AEN6321]]
- 1. [[Attaching SpecTcl to a ring buffer in compatibility mode|r6522#AEN6554]]
- 1. [[Running spectcldaq.server|r6563#AEN6616]]
- 2. [[Connecting to spectcldaq.server|r6563#AEN6621]]
- 1. [[Sample output from **ringbuffer status**|r6645#AEN6715]]
- 1. [[making hex dumps of data from a ring buffer.|r6743#AEN6794]]
- 1. [[Using stdintoring|r6797#AEN6846]]
- 1. [[Logging extension to readout gui|r7076#AEN7693]]
- 1. [[Dumping state changes and sampled event data with od|r7934#AEN8031]]
- 2. [[Dumping all but packet types|r7934#AEN8039]]
- 3. [[Attaching SpecTcl|r7934#AEN8047]]
- 1. [[Starting sclclient|r8051#AEN8177]]
- 1. [[Viewing a set of channel values interactively|r8201#AEN8235]]
- 2. [[Writing a set of channels to a file|r8201#AEN8238]]
- 3. [[Appending a set of channels to a file|r8201#AEN8241]]
- 4. [[Piping a set of channels to a program for processing|r8201#AEN8244]]
- 1. [[Supporting an observer in a snit type or widget|r9685#AEN9766]]
- 2. [[Supporting multiple observers in a snit type or widget|r9685#AEN9777]]
- 1. [[Creating a coypright notice on stderr|r10984#AEN11073]]
- 2. [[Creating an author credit on stderr|r10984#AEN11077]]
- 1. [[Using `CRingAccess` to connect to
                    a local ring.|r11458#AEN11636]]
- 2. [[Using `CRingAccess` to connect to a remote
                ring|r11458#AEN11640]]
- 1. [[Message filter predicate|r11644#AEN12397]]
- 1. [[Calling `CStringInteractor` specific
         members|r14888#AEN15045]]
- 1. [[evttclsh|r17843#AEN17944]]
- 1. [[Selecting sampled event from a ring.|r20487#AEN20756]]
- 1. [[Constructing a scaler item from an item gotten from a ring|r20784#AEN21108]]
- 1. [[Creating a begin run state transition item|r21133#AEN21441]]
- 1. [[evttclsh|r27434#AEN27535]]
- 1. [[evttclsh|r32681#AEN32782]]
- 1. [[Creating a CAENcard geographically|r36475#AEN37254]]
- 2. [[Setting a TDC to common stop mode|r36475#AEN37258]]
- 3. [[Reading out a CAEN 785 e.g.|r36475#AEN37262]]
- 1. [[Initializing branch 0|r37270#AEN37631]]
- 1. [[Using the LRS 1151 in the production readout framework.|r44118#AEN44202]]
- 1. [[Creating a device driver via private derivation|r45139#AEN45256]]
- 2. [[Creating a device driver via inclusion|r45139#AEN45262]]
- 1. [[Allocating a port with the port manager|r46170#AEN46304]]
- 2. [[Listing the port allocatiosn on a system.|r46170#AEN46308]]
- 1. [[Catching a CPortManagerException|r46317#AEN46453]]
- 1. [[AD811 configuration file example|r46491#AEN46544]]
- 1. [[LRS2228 creation example|r46940#AEN46994]]
- 1. [[The lrs2551 command|r47050#AEN47123]]
- 1. [[Using the **list** command to
                                  construct pedestals|r47126#AEN47226]]
- 2. [[Sample **ph7xxx** commands|r47126#AEN47316]]
- 1. [[Example of the **stack** command.|r47320#AEN47427]]
- 1. [[Listing CC-USB Serial numbers (Tcl).|r52051#AEN52714]]
- 2. [[Creating a CCCUSB object by serial number (Tcl).|r52051#AEN52724]]
- 1. [[Sample ADC commands|r53048#AEN53175]]
- 1. [[Using the **caenchain** command.|r53182#AEN53227]]
- 1. [[Configuring an SIS3820 scaler module|r53592#AEN53635]]
- 1. [[Configuring a CAEN V830 scaler|r53638#AEN53814]]
- 1. [[Configuring the SIS 3804 scaler|r53929#AEN53985]]
- 1. [[Sample Hytec 2530 configuration|r54134#AEN54265]]
- 1. [[Sample use of madc command|r54426#AEN54656]]
- 1. [[Building Stacks|r55210#AEN55335]]
- 1. [[Hooking update methods to recurring timer|r64142#AEN64213]]
- 1. [[Allocating a service port in Tcl|r64221#AEN64286]]
- 2. [[Listing allocated ports in Tcl|r64221#AEN64290]]
- 1. [[Action script example|r64351#AEN64465]]
- 2. [[Sequencer column configuration file|r64351#AEN64471]]
- 1. [[Creating and registering a V262 as a busy:|r64534#AEN64650]]
- 1. [[Deep iteration of `CCompondEventSegment` elements|r64763#AEN64973]]
- 2. [[Deep visitation of `CCompoundEventSegment` elements|r64763#AEN64977]]
- 1. [[Using the `CDocumentedPacket` class|r64985#AEN65240]]
- 1. [[Catching readout specific examples|r66003#AEN66020]]
- 1. [[Deep visitation in `CScalerBank` containers|r66027#AEN66261]]
- 1. [[Outputting the state of the run|r66553#AEN66650]]
- 1. [[Sample configuration file|r66858#AEN66956]]
- 1. [[Sample configuration file|r66964#AEN67072]]
- 1. [[Sample configuration file|r67080#AEN67088]]

---

|  |  |  |
| --- | --- | --- |
|  |  | Next |
|  |  | introduction |
