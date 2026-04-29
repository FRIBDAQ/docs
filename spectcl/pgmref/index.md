<a name="AEN1"></a># <a name="AEN2"></a>SpecTcl Programming Reference.

### <a name="AEN4"></a>Ron Fox


---

- **Table of Contents**
- 1. [[Introduction|c13]]
- I. [[SpecTclAPI class|p31]]
  - 2. [[SpecTcl|c33]]
  - [[SpecTcl|r37]] -- API Singleton class.
- II. [[Tree Parameter, Tree Variable API|p2427]]
  - 3. [[Tree parameter, tree variable API|c2429]]
  - [[CTreeParameter|r2438]] -- Parameter object 'independent' of rEvent
  - [[CTreeParameterArray|r3246]] -- Arrays of tree parameters
  - [[CTreeVariable|r3723]] -- Access to Tcl variables with metadata
  - [[CTreeVariableProperites|r4113]] -- Shared properties of CTreeVariable
  - [[CTreeVariableArray|r4290]] -- Container for an array of tree variables.
- III. [[Tcl++ classes|p4454]]
  - 4. [[Tcl++ classes|c4456]]
  - [[CTCLInterpreter|r4482]] -- 
              Encapsulate a Tcl interpreter.
  - [[CTCLInterpreterObject|r4718]] -- 
              Base class for objects that are associated with a Tcl Interpreter.
  - [[CTCLResult|r4797]] -- 
              Provide an object oriented interace to the Tcl interpreter result.
  - [[CTCLException|r4908]] -- 
              Class for reporting exceptional conditions in Tcl applications
              via the C++ try/catch mechanism.
  - [[CTCLObjectProcessor|r5051]] -- 
              Abstract base class to encapsulate the Tcl object command interface exposed by
              `Tcl_CreateObjCommand`.
  - [[CTCLProcessor|r5166]] -- 
              Provide `argc`, `argv`
              extension commands to Tcl.
  - [[CTCLCompatibiltyProcessor|r5356]] -- 
              Adaptor between `CTCLOjbectProcessor`
              and `CTCLProcessor`.
  - [[CTCLCommandPackage|r5423]] -- 
              Group several related Tcl command extensions and common services they
              may require together.
  - [[CTCLPackagedCommand|r5528]] -- 
              Base class for a command that lives in a `CTCLCommandPackage`
  - [[CTCLVariable|r5589]] -- 
              Encapsulate Tcl interpreter variables.
  - [[CTCLApplication 3|r5785]] -- 
              Base class for TCL/Tk applications.
  - [[CTCLHashTable|r5832]] -- 
              Object oriented interface to Tcl's hash table functions.
  - [[CTCLHashTableItem|r5963]] -- 
              Encapsulation of an entry in a Tcl Hash table as encapsulated
              in `CTCLHashTable`
  - [[CTCLHashTableIterator|r6031]] -- 
              Iterator for visiting all elements of a `CTCLHashTable`
  - [[CTCLString|r6127]] -- 
              Provide a wrapper for the Tcl_DString data type
              and its API
  - [[CTCLList|r6344]] -- 
              Provide access to Tcl List parsing.
  - [[CTCLChannel|r6453]] -- 
              Provide a C++ abstraction wrapper for Tcl Channels.
  - [[CTCLFileHandler|r6623]] -- 
              Base class for building object oriented Tcl File event handlers.
  - [[CTCLIdleProcess|r6709]] -- 
              Allows the establishment of an executable object that
              can be scheduled to be invoked when the Tcl/Tk intperpreter
              has no events that require processing.
  - [[CTCLTimer|r6770]] -- 
              Abstract base class for C++ objects attached to timer events.
  - [[CTCLLiveEventLoop|r6840]] -- Run Tcl with event loop.
  - [[CTCLChannelCommander|r6944]] -- Accept commands on a Tcl channel from the event loop.
  - [[CTCLStdioCommander|r7156]] -- Event driven command input on stdin/stdout
  - [[CTCLServer|r7220]] -- Listener for a Tcl server.
  - [[CTCLTcpServerInstance|r7348]] -- Channel commander that is a server instance for `CTCLServer`
  - [[CItemConfiguration|r7421]] -- Hold a configuration
  - [[CConfigurableObject|r8144]] -- Base class for objects tht have a configuration.
  - [[CTCLObjectPackage|r8364]] -- Provide common functionality for a set of
                  related commands.
  - [[CTCLPackagedObjectProcessor|r8426]] -- Base class for commands living in a
                      `CTCLObjectPackage`
- IV. [[Core SpecTcl classes|p8526]]
  - [[Extensible Factories|r8531]] -- Create factories that don't have hard-coded creationals.
  - [[CEventProcessor|r8643]] -- Abstract base class convering events to parameters
  - [[CEventBuilderEventProcessor|r8835]] -- Event processor for event built data.
  - [[CTclGrammerApp|r8944]] -- Base Application class
  - [[CHistogrammer|r9566]] -- SpecTcl histogramming core
  - [[Dictionaries|r10317]] -- Describe dictionaries used by SpecTcl
  - [[CAnalyzer|r10928]] -- Analyzer base class and classic analyzer
  - [[CTclAnalyzer|r11330]] -- Analyzer integrated with Tcl supporting pipeline
  - [[CBufferDecoder|r11884]] -- Base class for SpecTcl buffer decoders
  - [[CNSCLBufferDecoder|r12168]] -- Decode fixed sized event buffers from NSCLDAQ-7.x/8.x
  - [[CNSCLJumboBufferDecoder|r12328]] -- Decode NSCLDAQ 7.x/8.x buffers bigger than 128Kbytes.
  - [[CRingBufferDecoder|r12492]] -- Decode data from ring buffers
  - [[CRingFormatHelper|r12855]] -- ABC for4 ring buffer format helpers
  - [[CNamedItem|r13036]] -- Base class for items with names and ids.
  - [[CParameter|r13117]] -- Parameter definition.
  - [[CEvent|r13308]] -- Destination for decoded event data.
  - [[CSpectrum|r13461]] -- Classes implementing SpecTcl spectra
  - [[CFold|r15665]] -- Process gamma ray spectrum folds
  - [[CAxis|r15781]] -- Spectrum axis coordinate transforms.
  - [[CGate|r15893]] -- SpecTcl gate classes
  - [[CGateContainer|r17477]] -- Pointer like class for Gates.
  - [[CGateObserver|r17585]] -- Observe changes in the gate dictionary.
  - [[CFit|r17670]] -- Base class for spectrum fitting subsystem.
  - [[Predefined CFit classes|r17933]] -- 3SpecTcl
  - [[CSpectrumFit|r18101]] -- Fit of spectrum channels.
  - [[CFitFactory|r18284]] -- Creating fit objects by name
  - [[CFitDictionary|r18589]] -- Fitting subsystem dictionary.
  - [[CEventSink|r18861]] -- Base class for event sink pipeline elements
  - [[CEventFilter|r18923]] -- Abstract base class for event filters.
  - [[CGatedEventFilter|r19219]] -- Filter with output conditionalized on a gate check.
  - [[CFilterOutputStage|r19325]] -- Abstract base class for filter output streamers.
  - [[CWaveform|r19433]] -- Container for waveforms
  - [[CWaveformDictionary|r19570]] -- Singleton that holds SpecTcl's known waveforms
  - [[CXdrFilterOutputStage|r19676]] -- Filter output stage for writing Xdr filters.
  - [[CFilterOutputStageCreator|r19800]] -- Create filter output stages for
              `CFilterOutputStageFactory`
  - [[CFilterOutputStageFactory|r19862]] -- Create filter output stage objects.
  - [[CXdrFilterOutputStageCreator|r19929]] -- 
              Create `CXrFilterOutputStage` objects
  - [[FilterEventProcessor|r19943]] -- 
              Decodes events from a filter file into parameters.
  - [[CFold|r19957]] -- Process gamma ray spectrum folds
  - [[CAxis|r20073]] -- Spectrum axis coordinate transforms.
  - [[CGate|r20185]] -- SpecTcl gate classes
  - [[CGateContainer|r21769]] -- Pointer like class for Gates.
  - [[CGateObserver|r21877]] -- Observe changes in the gate dictionary.
  - [[CFit|r21962]] -- Base class for spectrum fitting subsystem.
  - [[Predefined CFit classes|r22225]] -- 3SpecTcl
  - [[CSpectrumFit|r22393]] -- Fit of spectrum channels.
  - [[CFitFactory|r22576]] -- Creating fit objects by name
  - [[CFitDictionary|r22881]] -- Fitting subsystem dictionary.
  - [[CEventSink|r23153]] -- Base class for event sink pipeline elements
  - [[CEventFilter|r23215]] -- Abstract base class for event filters.
  - [[Root tree building|r23256]] -- Classes to build root trees.
  - [[RootTreeSink|r23644]] -- Event sink that writes root trees.
  - [[RootEventProcessor|r23760]] -- Event processor to manage root event sinks
  - [[CPipelineManager|r23849]] -- v5.1+ Dynamic pipeline management
  - [[CPipelineEventProcessor|r24222]] -- Encapsulate an event processing pipeline as a processor.
- V. [[SpecTcl Displays|p24238]]
  - [[CDisplay|r24244]] -- Display interface base class
  - [[CNullDisplay|r24564]] -- Batch mode displayer
  - [[CXamine|r24577]] -- Displayer class for Xamine
  - [[Xamine Gates|r24810]] -- Represent gates in Xamine
  - [[XamineButton|r25142]] -- Describe a client button
  - [[CXamineButtonPrompt|r25288]] -- Base class for button prompter descriptions
  - [[CXamineNoPrompt|r25304]] -- Prompter that does not prompt
  - [[CXamineConfirmPrompt|r25316]] -- Prompt for confirmation
  - [[CXamineTextPrompt|r25329]] -- Prompt for a text string
  - [[CXamineSpectrumPrompt|r25341]] -- Prompt for a spectrum
  - [[CXamineFilePrompt|r25361]] -- Prompt for a filename.
  - [[CXaminePointsPrompt|r25373]] -- Prompt for points
  - [[CXamineEvent|r25388]] -- Encapsulate events from Xamine.
  - [[CButtonEvent|r25419]] -- Encapsulate button press events
  - [[CDisplayInterface|r25540]] -- Manages displayers
  - [[CDisplayCollection|r25661]] -- Maintain a named set of display objects.
  - [[CDisplayFactory|r25768]] -- Associate display creators with display type names
- VI. [[Callback based analysis framework.|p25862]]
  - [[CAnalysisEventProcessor|r25866]] -- Event processor for callback analysis.
  - [[CAnalysisBase|r25944]] -- Base class for callout objects
  - [[CAnalysisBase|r26046]] -- Base class for callout analyzers.

- **List of Examples**
- 1. [[evttclsh|r6840#AEN6941]]

---

|  |  |  |
| --- | --- | --- |
|  |  | Next |
|  |  | Introduction |
