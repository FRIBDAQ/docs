<a name="AEN1"></a># <a name="AEN1"></a>NSCL DAQ Software Documentation


---

**Table of Contents**I. [[p3]]1. [[c5]]1.1. [[c5#AEN15]]1.2. [[x123]]1.3. [[x180]]II. [[p263]]2. [[c265]]3. [[c292]]4. [[c318]]5. [[c342]]5.1. [[c342#AEN357]]5.2. [[x377]]III. [[p384]]6. [[c386]]7. [[c397]]7.1. [[c397#AEN411]]7.2. [[x479]]7.3. [[x513]]8. [[c656]]9. [[c669]]10. [[c707]][[r726]] -- Display epics channels11. [[c806]]12. [[c819]]13. [[c856]]14. [[c891]]15. [[c926]]16. [[c945]]16.1. [[c945#AEN973]]17. [[c1009]]17.1. [[c1009#AEN1022]]17.2. [[x1046]]17.3. [[x1065]]17.4. [[x1100]]18. [[c1105]]19. [[c1128]]20. [[c1153]]21. [[c1164]]22. [[c1194]]23. [[c1269]]24. [[c1288]]25. [[c1299]]25.1. [[c1299#AEN1304]]25.2. [[x1369]]IV. [[p1389]]26. [[c1391]]26.1. [[c1391#AEN1398]]26.2. [[x1415]]26.3. [[x1435]]27. [[c1472]]28. [[c1492]]29. [[c1553]]29.1. [[c1553#AEN1567]]29.2. [[x1590]]30. [[c1673]]31. [[c1688]]31.1. [[c1688#AEN1709]]31.2. [[x1719]]32. [[c1749]]32.1. [[c1749#AEN1762]]32.2. [[x1820]]33. [[c1839]]33.1. [[c1839#AEN1845]]33.2. [[x1859]]33.3. [[x1904]]34. [[c1972]]35. [[c2030]]35.1. [[c2030#AEN2040]]35.2. [[x2131]]35.3. [[x2142]]36. [[c2159]]37. [[c2217]]37.1. [[c2217#AEN2226]]37.2. [[x2240]]37.3. [[x2264]]37.4. [[x2297]]37.5. [[x2315]]37.6. [[x2405]]37.7. [[x2439]]38. [[c2475]]38.1. [[c2475#AEN2489]]38.2. [[x2716]]38.3. [[x2744]]38.4. [[x2825]]39. [[c2862]]39.1. [[c2862#AEN2865]]39.2. [[x2872]]39.3. [[x2888]]40. [[c2929]]40.1. [[c2929#AEN2950]]40.2. [[x2960]]41. [[c2990]]42. [[c3048]]42.1. [[c3048#AEN3069]]42.2. [[x3079]]43. [[c3109]]44. [[c3167]]44.1. [[c3167#AEN3181]]44.2. [[x3238]]45. [[c3251]]46. [[c3292]]46.1. [[c3292#AEN3304]]46.2. [[x3323]]47. [[c3342]]47.1. [[c3342#AEN3356]]47.2. [[x3388]]48. [[c3530]]V. [[p3542]]49. [[c3544]]49.1. [[c3544#AEN3557]]50. [[c3695]]VI. [[p3711]]51. [[c3713]]51.1. [[c3713#AEN3728]]51.2. [[x3733]]51.3. [[x3744]]51.4. [[x3810]]52. [[c3879]]52.1. [[c3879#AEN3899]]52.2. [[x4067]]52.3. [[x4112]]52.4. [[x4145]]53. [[c4231]]53.1. [[c4231#AEN4241]]53.2. [[x4248]][[f4252]][[r4255]] -- Start the event builder pipeline.[[r4320]] -- Stop the event builder pipeline.[[r4333]] -- Reset timestamp history[[r4347]] -- Flush event builder event queues.[[r4360]] -- Start a ring fragment source for the event builder.[[r4406]] -- Start S800 data source[[f4424]][[r4430]] -- Initialize the EZBuilder layer.[[r4483]] -- EZBuilder begin run actions[[r4502]] -- EZBuilder end run actions.[[r4516]] -- Event builder cilent framework[[r4560]] -- Submit event fragments.[[r4579]] -- Event builder input statistics[[r4627]] -- Get orderer output statistics[[r4646]] -- Get the late fragment statistics.[[r4674]] -- Bind scripts to data late events.[[r4698]] -- Supply a script to invoke on barrier events.[[r4718]] -- Create event source queues.[[r4736]] -- Mark a data source dead.[[r4751]] -- Revive all dead data sources associated with a socket[[r4766]] -- Empty all input queues.[[r4779]] -- Reset timestamp clocks.54. [[c4792]]54.1. [[c4792#AEN4803]]54.2. [[x5095]]54.3. [[x5110]]54.4. [[x5182]]54.5. [[x5198]]54.6. [[x5208]]55. [[c5213]]55.1. [[c5213#AEN5237]]55.2. [[x5253]]55.3. [[x5294]]55.4. [[x5455]]55.5. [[x5713]]55.6. [[x5726]]56. [[c5775]]56.1. [[c5775#AEN5801]]56.2. [[x5817]]56.3. [[x5848]]56.4. [[x6022]]56.5. [[x6256]]56.6. [[x6297]]56.7. [[x6339]]VII. [[p6393]]I. [[r6395]][[r6397]] -- Filter ring items to spectrodaq buffers[[r6435]] -- Create spectrodaq formatted event log files.[[r6475]] -- Provide event logger pipeline for use with ReadoutGUI.[[r6522]] -- Pipe data source for SpecTcl in spectrodaq buffer mode.[[r6563]] -- TCP/IP server of ring data in spectrodaq format.[[r6624]] -- Convert old buffered data to ring buffer format.II. [[r6643]][[r6645]] -- Manage ring buffers.[[r6743]] -- Transmit data from a ring buffer to stdout.[[r6797]] -- Pipe stdin to a ring buffer.[[r6849]] -- Tcl interpreter that always runs an event loop[[r6862]] -- Filter flattened fragments to ring items.[[r6940]] -- Glue event fragments together into events[[r6979]] -- Event builder ring fragment source from s800[[r7051]] -- Tee data to stdout and a ringbuffer.[[r7076]] -- Encapsulate data sources in a graphical user interface[[r7696]] -- Tcl interpreter that always runs an event loop[[r7709]] -- Tcl interpreter that always runs an event loop[[r7722]] -- Produce a formatted dump of event data.[[r7798]] -- Monitor essential programs[[r7873]] -- Record Event Data to Disk.[[r7934]] -- Provide selected ring data to non NSCL DAQ aware clients[[r8051]] -- Maintain scaler state in a tclserver[[r8185]] -- GUI Dump of ring buffer items.III. [[r8199]][[r8201]] -- Write a set of channels to file[[r8257]] -- 
            Push epics data into a Tcl Server (e.g. production readout).
        IV. [[r8356]][[r8358]] -- Display incomplete barrier statistics[[r8448]] -- Displays per queue barrier statistics[[r8517]] -- UI element to summarize barrier statistics.[[r8549]] -- Object that manages callback sets.[[r8629]] -- List event builder connections[[r8671]] -- Standard monitor UI procs.[[r8716]] -- Widget to display input statitics[[r8883]] -- Per queue input statistics widget[[r8976]] -- Display input queue statistics[[r9028]] -- Summary of input statistics.[[r9080]] -- Late fragment statistics[[r9151]] -- Widget to display summar of data late fragments.[[r9186]] -- Complete output statistics widget[[r9273]] -- Summarize output statistics[[r9329]] -- Key value pair widget[[r9424]] -- General key/widget sorted list[[r9551]] -- Event builder utility **proc**s[[r9685]] -- Support the Observer pattern[[r9784]] -- Event orderer compiled commands.V. [[r10013]][[r10015]] -- Access Rings from tcl.[[r10142]] -- locate specific SBS VME crate controllers.[[r10168]] -- CAMAC operation via a CES CAMAC interface[[r10193]] -- CAMAC operation via a Wiener VC32/CC32 board set[[r10218]] -- bcnaf via SBS VME CAMAC interfaces[[r10254]] -- GUI for controlling CAEN V812 CFD modules[[r10274]] -- Load settings in to a CAEN V812 CFD module.[[r10293]] -- Load setttings into an N568 shaper via SBS/V288.[[r10311]] -- GUI for the n568 shaper.[[r10334]] -- Control panel application for VHQ bias supply modules.[[r10350]] -- Canned VHS Control panel[[r10378]] -- Provide access to VME crates to Tcl scripts.[[r10485]] -- Manage TCP/IP service ports and advertise their allocations[[r10588]] -- Start a Tcl Server.[[r10631]] -- Control tcl server authorization.[[r10677]] -- Command line tool to burn NSCLDAQ data DVDs.[[r10704]] -- Graphical front end to dvdburn[[r10722]] -- Live Scaler DisplaysVI. [[r10940]][[r10942]] -- Start an event readout program.VII. [[r10982]][[r10984]] -- Generate license/author credits.[[r11080]] -- Integer byte order conversions[[r11266]] -- RingMaster access.[[r11458]] -- Remote Ring Access[[r11644]] -- Low level ring buffer primitives[[r12452]] -- Abstract base class for the exception class hierarchy.[[r12539]] -- Exceptions that wrap the Unix `errno`[[r12616]] -- Reports and exception for a value out of allowed range.[[r12754]] -- Exception for invalid state transitions.[[r12853]] -- I/O error on a C++ stream.[[r13016]] -- Report errors in universal resource identifiers (uri)s.[[r13201]] -- Exceptions for synchronization class abuse.[[r13336]] -- Report invalid function arguments.[[r13470]] -- class description[[r13796]] -- Abstract base authenticator class.[[r13900]] -- Authenticate against a stored password.[[r14088]] -- Authenticate against a unix user name and password.[[r14299]] -- Authenticate against a Tcl List.[[r14397]] -- Authenticate against a list of allowed credentials.[[r14539]] -- Authenticate from a list of TCP/IP hosts[[r14719]] -- Base class for security interactions.[[r14888]] -- Provide an interactor that processes strings.[[r15049]] -- Interact with  file descriptor[[r15175]] -- Separate prompt and input interactors.[[r15300]] -- 
            Base class for TCL/Tk applications.
        [[r15343]] -- 
            Class for reporting exceptional conditions in Tcl applications
            via the C++ try/catch mechanism.
        [[r15486]] -- 
            Encapsulate a Tcl interpreter.
        [[r15704]] -- 
            Base class for objects that are associated with a Tcl Interpreter.
        [[r15783]] -- 
            Provide access to Tcl List parsing.
        [[r15892]] -- 
            Encapsulate Tcl Dual ported objects.
        [[r16123]] -- 
            Abstract base class to encapsulate the Tcl object command interface exposed by
            `Tcl_CreateObjCommand`.
        [[r16216]] -- 
            Encapsulate Tcl interpreter variables.
        [[r16411]] -- 
            Provide `argc`, `argv`
            extension commands to Tcl.
        [[r16600]] -- 
            Provide a C++ abstraction wrapper for Tcl Channels.
        [[r16770]] -- 
            Group several related Tcl command extensions and common services they
            may require together.
        [[r16875]] -- 
            Adaptor between `CTCLOjbectProcessor`
            and `CTCLProcessor`.
        [[r16942]] -- 
            Base class for building object oriented Tcl File event handlers.
        [[r17028]] -- 
            Object oriented interface to Tcl's hash table functions.
        [[r17159]] -- 
            Encapsulation of an entry in a Tcl Hash table as encapsulated
            in `CTCLHashTable`
[[r17227]] -- 
            Iterator for visiting all elements of a `CTCLHashTable`
[[r17323]] -- 
            Allows the establishment of an executable object that
            can be scheduled to be invoked when the Tcl/Tk intperpreter
            has no events that require processing.
        [[r17384]] -- 
            Base class for a command that lives in a `CTCLCommandPackage`
[[r17445]] -- 
            Provide an object oriented interace to the Tcl interpreter result.
        [[r17556]] -- 
            Provide a wrapper for the Tcl_DString data type
            and its API
        [[r17773]] -- 
            Abstract base class for C++ objects attached to timer events.
        [[r17843]] -- Run Tcl with event loop.[[r17947]] -- Accept commands on a Tcl channel from the event loop.[[r18159]] -- Event driven command input on stdin/stdout[[r18223]] -- Listener for a Tcl server.[[r18351]] -- Channel commander that is a server instance for `CTCLServer`[[r18424]] -- Provide common functionality for a set of
                related commands.[[r18486]] -- Base class for commands living in a
                    `CTCLObjectPackage`
[[r18586]] -- Hold a configuration[[r19309]] -- Base class for objects tht have a configuration.[[r19529]] -- Abstract base class for thread objects.[[r19663]] -- Wait queue for threads[[r19761]] -- Provide Critical Regions, Monitors[[r19928]] -- Parse Uniform Resource Identifiers (URI)[[r20076]] -- Framework event builder client application.[[r20220]] -- Event builder client framework.[[r20276]] -- Client of the event orderer[[r20487]] -- Encapsulates an item in a ring buffer.[[r20784]] -- Encapsulate ring buffer scaler items.[[r21133]] -- Encapsulate a ring buffer state change item.[[r21444]] -- Encapsulate ring items that are lists of text strings.[[r21671]] -- Provides statistics regarding the number of events produced.[[r21906]] -- Encapsulate a EVB_FRAGMENT ring item
         [[r22179]] -- Base class for predicates that select items from
            ring buffers.[[r22510]] -- Select all ring items except some.[[r22685]] -- Only accept specified ring item types.[[r22849]] -- Format of ring items.[[r23303]] -- Functions to create ring items.[[r23559]] -- Abstract base class of data source for ring items.[[r23600]] -- Ringbuffer data source for ring items.[[r23668]] -- Ring item data source from a file[[r23725]] -- Create data sources given a URI[[r23781]] -- Upcast ring items to specific ring item objects.[[r23873]] -- Abstract base class for the exception class hierarchy.[[r23960]] -- Exceptions that wrap the Unix `errno`[[r24037]] -- Reports and exception for a value out of allowed range.[[r24175]] -- Exception for invalid state transitions.[[r24274]] -- I/O error on a C++ stream.[[r24437]] -- Report errors in universal resource identifiers (uri)s.[[r24622]] -- Exceptions for synchronization class abuse.[[r24757]] -- Report invalid function arguments.[[r24891]] -- 
            Base class for TCL/Tk applications.
        [[r24934]] -- 
            Class for reporting exceptional conditions in Tcl applications
            via the C++ try/catch mechanism.
        [[r25077]] -- 
            Encapsulate a Tcl interpreter.
        [[r25295]] -- 
            Base class for objects that are associated with a Tcl Interpreter.
        [[r25374]] -- 
            Provide access to Tcl List parsing.
        [[r25483]] -- 
            Encapsulate Tcl Dual ported objects.
        [[r25714]] -- 
            Abstract base class to encapsulate the Tcl object command interface exposed by
            `Tcl_CreateObjCommand`.
        [[r25807]] -- 
            Encapsulate Tcl interpreter variables.
        [[r26002]] -- 
            Provide `argc`, `argv`
            extension commands to Tcl.
        [[r26191]] -- 
            Provide a C++ abstraction wrapper for Tcl Channels.
        [[r26361]] -- 
            Group several related Tcl command extensions and common services they
            may require together.
        [[r26466]] -- 
            Adaptor between `CTCLOjbectProcessor`
            and `CTCLProcessor`.
        [[r26533]] -- 
            Base class for building object oriented Tcl File event handlers.
        [[r26619]] -- 
            Object oriented interface to Tcl's hash table functions.
        [[r26750]] -- 
            Encapsulation of an entry in a Tcl Hash table as encapsulated
            in `CTCLHashTable`
[[r26818]] -- 
            Iterator for visiting all elements of a `CTCLHashTable`
[[r26914]] -- 
            Allows the establishment of an executable object that
            can be scheduled to be invoked when the Tcl/Tk intperpreter
            has no events that require processing.
        [[r26975]] -- 
            Base class for a command that lives in a `CTCLCommandPackage`
[[r27036]] -- 
            Provide an object oriented interace to the Tcl interpreter result.
        [[r27147]] -- 
            Provide a wrapper for the Tcl_DString data type
            and its API
        [[r27364]] -- 
            Abstract base class for C++ objects attached to timer events.
        [[r27434]] -- Run Tcl with event loop.[[r27538]] -- Accept commands on a Tcl channel from the event loop.[[r27750]] -- Event driven command input on stdin/stdout[[r27814]] -- Listener for a Tcl server.[[r27942]] -- Channel commander that is a server instance for `CTCLServer`[[r28015]] -- Provide common functionality for a set of
                related commands.[[r28077]] -- Base class for commands living in a
                    `CTCLObjectPackage`
[[r28177]] -- Hold a configuration[[r28900]] -- Base class for objects tht have a configuration.[[r29120]] -- Abstract base class for the exception class hierarchy.[[r29207]] -- Exceptions that wrap the Unix `errno`[[r29284]] -- Reports and exception for a value out of allowed range.[[r29422]] -- Exception for invalid state transitions.[[r29521]] -- I/O error on a C++ stream.[[r29684]] -- Report errors in universal resource identifiers (uri)s.[[r29869]] -- Exceptions for synchronization class abuse.[[r30004]] -- Report invalid function arguments.[[r30138]] -- 
            Base class for TCL/Tk applications.
        [[r30181]] -- 
            Class for reporting exceptional conditions in Tcl applications
            via the C++ try/catch mechanism.
        [[r30324]] -- 
            Encapsulate a Tcl interpreter.
        [[r30542]] -- 
            Base class for objects that are associated with a Tcl Interpreter.
        [[r30621]] -- 
            Provide access to Tcl List parsing.
        [[r30730]] -- 
            Encapsulate Tcl Dual ported objects.
        [[r30961]] -- 
            Abstract base class to encapsulate the Tcl object command interface exposed by
            `Tcl_CreateObjCommand`.
        [[r31054]] -- 
            Encapsulate Tcl interpreter variables.
        [[r31249]] -- 
            Provide `argc`, `argv`
            extension commands to Tcl.
        [[r31438]] -- 
            Provide a C++ abstraction wrapper for Tcl Channels.
        [[r31608]] -- 
            Group several related Tcl command extensions and common services they
            may require together.
        [[r31713]] -- 
            Adaptor between `CTCLOjbectProcessor`
            and `CTCLProcessor`.
        [[r31780]] -- 
            Base class for building object oriented Tcl File event handlers.
        [[r31866]] -- 
            Object oriented interface to Tcl's hash table functions.
        [[r31997]] -- 
            Encapsulation of an entry in a Tcl Hash table as encapsulated
            in `CTCLHashTable`
[[r32065]] -- 
            Iterator for visiting all elements of a `CTCLHashTable`
[[r32161]] -- 
            Allows the establishment of an executable object that
            can be scheduled to be invoked when the Tcl/Tk intperpreter
            has no events that require processing.
        [[r32222]] -- 
            Base class for a command that lives in a `CTCLCommandPackage`
[[r32283]] -- 
            Provide an object oriented interace to the Tcl interpreter result.
        [[r32394]] -- 
            Provide a wrapper for the Tcl_DString data type
            and its API
        [[r32611]] -- 
            Abstract base class for C++ objects attached to timer events.
        [[r32681]] -- Run Tcl with event loop.[[r32785]] -- Accept commands on a Tcl channel from the event loop.[[r32997]] -- Event driven command input on stdin/stdout[[r33061]] -- Listener for a Tcl server.[[r33189]] -- Channel commander that is a server instance for `CTCLServer`[[r33262]] -- Provide common functionality for a set of
                related commands.[[r33324]] -- Base class for commands living in a
                    `CTCLObjectPackage`
[[r33424]] -- Hold a configuration[[r34147]] -- Base class for objects tht have a configuration.[[r34367]] -- Class wrapping of the SBS VME library.[[r34682]] -- Provide access to SBS/Bit3 driver parameters.[[r35231]] -- Reference counted pointer like object to VME address segments.[[r35632]] -- Provide a base set of services for a VME module driver class.[[r35957]] -- Report errors in memory mapping requests.[[r36013]] -- Support the Hytec NADC 2530 Peak sensing ADC.[[r36475]] -- Support for the CAEN 32 bit digitizers[[r37270]] -- CES CBD 8210 CAMAC branch highway driver (obsolete)[[r37638]] -- Support for the CAEN V1190 and V1290
                    multihit, complicated TDC.[[r40020]] -- Support the CCAENV560 non-latching scaler.[[r40184]] -- Support driver for the CAEN V820/V830 latching scaler module.[[r40741]] -- Software support for the CAEN V977 I/O register.[[r41140]] -- Support software for the LeCroy LRS 2551 12 channel CAMAC scaler[[r41250]] -- High level support software for the 32 channel LeCroy LRS 4434 CAMAC scaler module[[r41362]] -- Provide computer busy status support for the BiRA CAMAC
                NIM out module.
            [[r41470]] -- Trigger module for the CES CBD 8210 VME CAMAC Parallel Branch Highway Driver
            [[r41524]] -- Manages CAMAC memory maps.[[r41606]] -- Provide support for a generic CAMAC module.[[r41980]] -- Provides low level support for the BiRa CAMAC Nim output module.[[r42069]] -- Encapsulation of a BiRa 1302 CAMAC controller via CES CBS8210.[[r42409]] -- Support for the SIS 3600 VME latch module.[[r42868]] -- Low level support for SIS 3820 32 channel latching scaler module[[r43574]] -- Abstract base class for reading scalers into a vector[[r43681]] -- Abstract base class for status modules.[[r43746]] -- Abstract base class for triggers[[r43774]] -- Pointer like object for accessing the VME[[r44118]] -- High level support for the LeCroy LRS 1151 VME scaler.[[r44205]] -- Implement a status module using the CAEN V262 module.[[r44289]] -- VME trigger class based on the CAEN V262 I/O module.[[r44340]] -- [[r44683]] -- Support for the CAEN V262 I/O register module.[[r44830]] -- Exception that can be thrown in the event of memory mapping errors.[[r44865]] -- Low level support for the BiRa VME nim output module[[r45139]] -- Convenience base class for implementing VME module support[[r45437]] -- Low Level support for the SIS 3300 Flash ADC module[[r46170]] -- Provide a C++ interface to the server port manager daemon.[[r46317]] -- Report errors conditions in port manager transactionsVIII. [[r46463]][[r46465]] -- Register Tcl command ensemble as a device module[[r46491]] -- Support the Ortec AD811 ADC[[r46547]] -- Manage CAEN C1205 QDC modules.[[r46667]] -- Manages the C257 scaler module[[r46740]] -- Configure and read scalers from CC-USB module[[r46940]] -- Manages the LRS2228 TDC[[r46997]] -- Manage LeCroy 2249 QDC modules[[r47050]] -- Manage LRS 2551 modules[[r47126]] -- Define Phillips ADC/TDC/QDC modules[[r47320]] -- Create and configure CC-USB stacks.[[r47448]] -- Create and manipulate slow control device instances[[r47490]] -- TCP/IP slow control protocol[[r47601]] -- Provide access to a CC-USB device.[[r50336]] -- Create lists of CAMAC commands for CC-USB controllers.[[r50799]] -- base class for devices that have a configuration[[r52051]] -- Swig wrapping of the CCCUSB C++ class.[[r52779]] -- Tcl wrapping of `CCCUSBReadoutList`IX. [[r53046]][[r53048]] -- Create/configure CAEN V775, V785, V792, V862 modules.[[r53182]] -- Aggregate adc modules into CBLT readout chains.[[r53231]] -- Control VM-USB resources and read internal scalers[[r53428]] -- Driver for SIS3300/1 FADC[[r53592]] -- Create and configure SIS 3820 scaler modules[[r53638]] -- Create and configure CAEN V830 32 channel scalers.[[r53817]] -- Create and configure CAEN V977 Input registers[[r53929]] -- Create and configure SIS 3804 scalers[[r53988]] -- XLM-XXV with Wash-U HINP firmware.[[r54047]] -- XLM with Wash-U pulse shape discrmination firmware[[r54082]] -- Pair up to 2 XLMs and FADC for HiRA[[r54134]] -- Support the Hytec NADC 2530 adc module.[[r54289]] -- tcl driver support functions.[[r54426]] -- Acquire events from Mesytec MADC32 ADC.[[r54677]] -- Support CBLT chains of MADC32 modules.[[r54738]] -- Support dead-time counters in MADC32 as scalers.[[r54775]] -- Support for XLM with MASE firmware.[[r54825]] -- Provide support for the CAEN V1x90 TDC family.[[r55080]] -- CAENV1729a waveform digitizer.[[r55210]] -- Compose and configure VM-USB readout stacks.[[r55338]] -- Interface with VM-USB controller.[[r57342]] -- Construct VM-USB stacks[[r58237]] -- Execute lists remotely on VMUSBReadout[[r59464]] -- Configuration database[[r60631]] -- SWIG Tcl wrapping of `CVMUSB`[[r61379]] -- SWIG wrappers for `CVMUSBReadoutList`
[[r61869]] -- control config command: create/configure modules.[[r62123]] -- Watch variables (slow controls)[[r62142]] -- VMUSB Slow controls protocolX. [[r62204]][[r62206]] -- s800 Readout Callouts module[[r62291]] -- Access CAENnet from Tcl scripts.[[r62356]] -- Provide access to CES CBD8210 CAMAC to Tcl scripts[[r62523]] -- Tcl Script CAMAC access via VC32/CC32 boardset.[[r62661]] -- low level control of the CAEN V812 CFD[[r62801]] -- Megawidget control panel for the CAEN V812 CFD[[r62933]] -- Support package for the CAEN N568B shaper.[[r63121]] -- Control panel megawidget for N568 shaping amplifier[[r63258]] -- Low level Tcl access to iSEG VHQ2xxx units.[[r63445]] -- Control widget for iSeg vhq2xx VME bias supply.[[r63638]] -- SBS support for VHS 404 modules.[[r64142]] -- User interface components for VHS 404 power supplies.[[r64221]] -- Tcl API for the DaqPortManager daemon.[[r64299]] -- Burn NSCL Data to DVD[[r64351]] -- 
            Provide a ReadoutGui plugin for nscldaq 8.1 and later that can
            automate several data taking runs.
        XI. [[r64477]][[r64479]] -- Abstract base class for Busy module management.[[r64534]] -- Concrete busy class for the CAEN V262 input module.[[r64659]] -- Trigger module with CAEN V262[[r64763]] -- Container for other event segments[[r64985]] -- Encapsulate event data in a packet that is documented.[[r65248]] -- Encapsulate an event segment in a documented packet.[[r65366]] -- Base class for all event segments.[[r65545]] -- Abstract base class for triggers.[[r65600]] -- Encapsulate the experiment.[[r65873]] -- Exception thrown by documented packets.[[r65983]] -- A trigger that never fires.[[r66003]] -- Base class for readout specific exceptions[[r66027]] -- Container for individual Scaler objects.[[r66269]] -- CEventTrigger that fires periodically[[r66357]] -- Concrete busy class using the CAEN V977 module[[r66459]] -- Concrete Trigger class using CAEN V977 module.[[r66553]] -- Encapsulate important state of the software.[[r66653]] -- Base class for scaler readout classesXII. [[r66739]][[r66741]] -- Event orderer protocolXIII. [[r66856]][[r66858]] -- Format of configuration files for CAENV 812 software.[[r66964]] -- N568 shaper configuration file[[r67080]] --  Config file for

**List of Tables**7-1. [[x513#AEN575]]7-2. [[x513#AEN596]]7-3. [[x513#AEN616]]47-1. [[x3388#AEN3392]]

**List of Figures**7-1. [[x479#AEN495]]

**List of Examples**2-1. [[c265#AEN278]]2-2. [[c265#AEN284]]5-1. [[c342#AEN366]]5-2. [[c342#AEN370]]5-3. [[c342#AEN374]]5-4. [[x377#AEN381]]7-1. [[x513#AEN561]]15-1. [[c926#AEN941]]16-1. [[c945#AEN959]]16-2. [[c945#AEN963]]16-3. [[c945#AEN976]]16-4. [[c945#AEN981]]16-5. [[c945#AEN986]]16-6. [[c945#AEN992]]16-7. [[c945#AEN998]]16-8. [[c945#AEN1003]]17-1. [[c1009#compatibilitybuffer-ex1]]17-2. [[c1009#AEN1030]]17-3. [[x1046#AEN1060]]17-4. [[x1065#AEN1080]]18-1. [[c1105#AEN1122]]19-1. [[c1128#AEN1137]]19-2. [[c1128#AEN1143]]19-3. [[c1128#AEN1149]]21-1. [[c1164#AEN1189]]22-1. [[c1194#AEN1247]]22-2. [[c1194#AEN1255]]22-3. [[c1194#AEN1263]]25-1. [[c1299#AEN1349]]26-1. [[c1391#AEN1401]]26-2. [[c1391#AEN1407]]26-3. [[c1391#AEN1411]]26-4. [[x1415#AEN1428]]27-1. [[c1472#AEN1481]]27-2. [[c1472#AEN1484]]27-3. [[c1472#AEN1487]]28-1. [[c1492#AEN1500]]28-2. [[c1492#AEN1508]]28-3. [[c1492#AEN1540]]28-4. [[c1492#AEN1543]]28-5. [[c1492#AEN1547]]29-1. [[c1553#AEN1574]]29-2. [[c1553#AEN1580]]29-3. [[c1553#AEN1586]]29-4. [[x1590#AEN1604]]29-5. [[x1590#AEN1653]]30-1. [[c1673#AEN1680]]31-1. [[x1719#AEN1744]]32-1. [[c1749#AEN1790]]32-2. [[x1820#AEN1831]]32-3. [[x1820#AEN1835]]33-1. [[c1839#AEN1852]]33-2. [[c1839#AEN1856]]33-3. [[x1859#AEN1863]]35-1. [[c2030#AEN2053]]35-2. [[c2030#AEN2085]]35-3. [[c2030#AEN2109]]35-4. [[x2131#AEN2139]]36-1. [[c2159#AEN2187]]36-2. [[c2159#AEN2213]]37-1. [[x2264#AEN2267]]37-2. [[x2297#AEN2312]]37-3. [[x2405#AEN2416]]37-4. [[x2439#AEN2447]]37-5. [[x2439#AEN2464]]38-1. [[x2744#AEN2750]]38-2. [[x2744#AEN2757]]38-3. [[x2744#AEN2762]]39-1. [[x2888#AEN2905]]40-1. [[x2960#AEN2985]]42-1. [[x3079#AEN3104]]47-1. [[x3388#AEN3526]]49-1. [[c3544#AEN3579]]49-2. [[c3544#AEN3594]]49-3. [[c3544#AEN3608]]49-4. [[c3544#AEN3660]]49-5. [[c3544#AEN3670]]49-6. [[c3544#AEN3681]]51-1. [[x3744#AEN3749]]52-1. [[c3879#AEN3925]]52-2. [[c3879#AEN3957]]52-3. [[c3879#AEN3971]]52-4. [[c3879#AEN3984]]52-5. [[c3879#AEN4028]]52-6. [[x4067#AEN4078]]52-7. [[x4145#AEN4184]]54-1. [[x5095#AEN5100]]55-1. [[x5253#AEN5257]]55-2. [[x5253#AEN5280]]55-3. [[x5253#AEN5291]]55-4. [[x5294#AEN5299]]55-5. [[x5294#AEN5305]]55-6. [[x5455#AEN5502]]55-7. [[x5455#AEN5599]]55-8. [[x5455#AEN5710]]56-1. [[x5817#AEN5821]]56-2. [[x5817#AEN5833]]56-3. [[x5817#AEN5842]]56-4. [[x5848#AEN5856]]56-5. [[x5848#AEN5865]]56-6. [[x5848#AEN5927]]56-7. [[x5848#AEN5946]]56-8. [[x5848#AEN5972]]56-9. [[x6022#AEN6045]]56-10. [[x6022#AEN6137]]56-11. [[x6022#AEN6242]]56-12. [[x6297#AEN6321]]1. [[r6522#AEN6554]]1. [[r6563#AEN6616]]2. [[r6563#AEN6621]]1. [[r6645#AEN6715]]1. [[r6743#AEN6794]]1. [[r6797#AEN6846]]1. [[r7076#AEN7693]]1. [[r7934#AEN8031]]2. [[r7934#AEN8039]]3. [[r7934#AEN8047]]1. [[r8051#AEN8177]]1. [[r8201#AEN8235]]2. [[r8201#AEN8238]]3. [[r8201#AEN8241]]4. [[r8201#AEN8244]]1. [[r9685#AEN9766]]2. [[r9685#AEN9777]]1. [[r10984#AEN11073]]2. [[r10984#AEN11077]]1. [[r11458#AEN11636]]2. [[r11458#AEN11640]]1. [[r11644#AEN12397]]1. [[r14888#AEN15045]]1. [[r17843#AEN17944]]1. [[r20487#AEN20756]]1. [[r20784#AEN21108]]1. [[r21133#AEN21441]]1. [[r27434#AEN27535]]1. [[r32681#AEN32782]]1. [[r36475#AEN37254]]2. [[r36475#AEN37258]]3. [[r36475#AEN37262]]1. [[r37270#AEN37631]]1. [[r44118#AEN44202]]1. [[r45139#AEN45256]]2. [[r45139#AEN45262]]1. [[r46170#AEN46304]]2. [[r46170#AEN46308]]1. [[r46317#AEN46453]]1. [[r46491#AEN46544]]1. [[r46940#AEN46994]]1. [[r47050#AEN47123]]1. [[r47126#AEN47226]]2. [[r47126#AEN47316]]1. [[r47320#AEN47427]]1. [[r52051#AEN52714]]2. [[r52051#AEN52724]]1. [[r53048#AEN53175]]1. [[r53182#AEN53227]]1. [[r53592#AEN53635]]1. [[r53638#AEN53814]]1. [[r53929#AEN53985]]1. [[r54134#AEN54265]]1. [[r54426#AEN54656]]1. [[r55210#AEN55335]]1. [[r64142#AEN64213]]1. [[r64221#AEN64286]]2. [[r64221#AEN64290]]1. [[r64351#AEN64465]]2. [[r64351#AEN64471]]1. [[r64534#AEN64650]]1. [[r64763#AEN64973]]2. [[r64763#AEN64977]]1. [[r64985#AEN65240]]1. [[r66003#AEN66020]]1. [[r66027#AEN66261]]1. [[r66553#AEN66650]]1. [[r66858#AEN66956]]1. [[r66964#AEN67072]]1. [[r67080#AEN67088]]

---

|  |  |  |
| --- | --- | --- |
|  |  | Next |
|  |  | introduction |
