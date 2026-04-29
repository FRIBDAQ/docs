<a name="AEN1"></a># <a name="AEN2"></a>SpecTcl Programming Reference.

### <a name="AEN4"></a>Ron Fox


---

- **Table of Contents**
- 1. [[Introduction|c13]]
- I. [[SpecTclAPI class|p31]]
  - 2. [[SpecTcl|c33]]
  - [[SpecTcl|r37]] -- API Singleton class.
- II. [[Tree Parameter, Tree Variable API|p2375]]
  - 3. [[Tree parameter, tree variable API|c2377]]
  - [[CTreeParameter|r2386]] -- Parameter object 'independent' of rEvent
  - [[CTreeParameterArray|r3194]] -- Arrays of tree parameters
  - [[CTreeVariable|r3671]] -- Access to Tcl variables with metadata
  - [[CTreeVariableProperites|r4061]] -- Shared properties of CTreeVariable
  - [[CTreeVariableArray|r4238]] -- Container for an array of tree variables.
- III. [[Tcl++ classes|p4402]]
  - 4. [[Tcl++ classes|c4404]]
  - [[CTCLInterpreter|r4430]] -- 
              Encapsulate a Tcl interpreter.
  - [[CTCLInterpreterObject|r4666]] -- 
              Base class for objects that are associated with a Tcl Interpreter.
  - [[CTCLResult|r4745]] -- 
              Provide an object oriented interace to the Tcl interpreter result.
  - [[CTCLException|r4856]] -- 
              Class for reporting exceptional conditions in Tcl applications
              via the C++ try/catch mechanism.
  - [[CTCLObjectProcessor|r4999]] -- 
              Abstract base class to encapsulate the Tcl object command interface exposed by
              `Tcl_CreateObjCommand`.
  - [[CTCLProcessor|r5114]] -- 
              Provide `argc`, `argv`
              extension commands to Tcl.
  - [[CTCLCompatibiltyProcessor|r5304]] -- 
              Adaptor between `CTCLOjbectProcessor`
              and `CTCLProcessor`.
  - [[CTCLCommandPackage|r5371]] -- 
              Group several related Tcl command extensions and common services they
              may require together.
  - [[CTCLPackagedCommand|r5476]] -- 
              Base class for a command that lives in a `CTCLCommandPackage`
  - [[CTCLVariable|r5537]] -- 
              Encapsulate Tcl interpreter variables.
  - [[CTCLApplication 3|r5733]] -- 
              Base class for TCL/Tk applications.
  - [[CTCLHashTable|r5780]] -- 
              Object oriented interface to Tcl's hash table functions.
  - [[CTCLHashTableItem|r5911]] -- 
              Encapsulation of an entry in a Tcl Hash table as encapsulated
              in `CTCLHashTable`
  - [[CTCLHashTableIterator|r5979]] -- 
              Iterator for visiting all elements of a `CTCLHashTable`
  - [[CTCLString|r6075]] -- 
              Provide a wrapper for the Tcl_DString data type
              and its API
  - [[CTCLList|r6292]] -- 
              Provide access to Tcl List parsing.
  - [[CTCLChannel|r6401]] -- 
              Provide a C++ abstraction wrapper for Tcl Channels.
  - [[CTCLFileHandler|r6571]] -- 
              Base class for building object oriented Tcl File event handlers.
  - [[CTCLIdleProcess|r6657]] -- 
              Allows the establishment of an executable object that
              can be scheduled to be invoked when the Tcl/Tk intperpreter
              has no events that require processing.
  - [[CTCLTimer|r6718]] -- 
              Abstract base class for C++ objects attached to timer events.
  - [[CTCLLiveEventLoop|r6788]] -- Run Tcl with event loop.
  - [[CTCLChannelCommander|r6892]] -- Accept commands on a Tcl channel from the event loop.
  - [[CTCLStdioCommander|r7104]] -- Event driven command input on stdin/stdout
  - [[CTCLServer|r7168]] -- Listener for a Tcl server.
  - [[CTCLTcpServerInstance|r7296]] -- Channel commander that is a server instance for `CTCLServer`
  - [[CItemConfiguration|r7369]] -- Hold a configuration
  - [[CConfigurableObject|r8092]] -- Base class for objects tht have a configuration.
  - [[CTCLObjectPackage|r8312]] -- Provide common functionality for a set of
                  related commands.
  - [[CTCLPackagedObjectProcessor|r8374]] -- Base class for commands living in a
                      `CTCLObjectPackage`
- IV. [[Core SpecTcl classes|p8474]]
  - [[Extensible Factories|r8479]] -- Create factories that don't have hard-coded creationals.
  - [[CEventProcessor|r8591]] -- Abstract base class convering events to parameters
  - [[CEventBuilderEventProcessor|r8783]] -- Event processor for event built data.
  - [[CTclGrammerApp|r8892]] -- Base Application class
  - [[CHistogrammer|r9514]] -- SpecTcl histogramming core
  - [[Dictionaries|r10265]] -- Describe dictionaries used by SpecTcl
  - [[CAnalyzer|r10876]] -- Analyzer base class and classic analyzer
  - [[CTclAnalyzer|r11278]] -- Analyzer integrated with Tcl supporting pipeline
  - [[CBufferDecoder|r11832]] -- Base class for SpecTcl buffer decoders
  - [[CNSCLBufferDecoder|r12116]] -- Decode fixed sized event buffers from NSCLDAQ-7.x/8.x
  - [[CNSCLJumboBufferDecoder|r12276]] -- Decode NSCLDAQ 7.x/8.x buffers bigger than 128Kbytes.
  - [[CRingBufferDecoder|r12440]] -- Decode data from ring buffers
  - [[CRingFormatHelper|r12803]] -- ABC for4 ring buffer format helpers
  - [[CNamedItem|r12984]] -- Base class for items with names and ids.
  - [[CParameter|r13065]] -- Parameter definition.
  - [[CEvent|r13256]] -- Destination for decoded event data.
  - [[CSpectrum|r13409]] -- Classes implementing SpecTcl spectra
  - [[CFold|r15613]] -- Process gamma ray spectrum folds
  - [[CAxis|r15729]] -- Spectrum axis coordinate transforms.
  - [[CGate|r15841]] -- SpecTcl gate classes
  - [[CGateContainer|r17425]] -- Pointer like class for Gates.
  - [[CGateObserver|r17533]] -- Observe changes in the gate dictionary.
  - [[CFit|r17618]] -- Base class for spectrum fitting subsystem.
  - [[Predefined CFit classes|r17881]] -- 3SpecTcl
  - [[CSpectrumFit|r18049]] -- Fit of spectrum channels.
  - [[CFitFactory|r18232]] -- Creating fit objects by name
  - [[CFitDictionary|r18537]] -- Fitting subsystem dictionary.
  - [[CEventSink|r18809]] -- Base class for event sink pipeline elements
  - [[CEventFilter|r18871]] -- Abstract base class for event filters.
  - [[CGatedEventFilter|r19167]] -- Filter with output conditionalized on a gate check.
  - [[CFilterOutputStage|r19273]] -- Abstract base class for filter output streamers.
  - [[CXdrFilterOutputStage|r19381]] -- Filter output stage for writing Xdr filters.
  - [[CFilterOutputStageCreator|r19505]] -- Create filter output stages for
              `CFilterOutputStageFactory`
  - [[CFilterOutputStageFactory|r19567]] -- Create filter output stage objects.
  - [[CXdrFilterOutputStageCreator|r19634]] -- 
              Create `CXrFilterOutputStage` objects
  - [[FilterEventProcessor|r19648]] -- 
              Decodes events from a filter file into parameters.
  - [[CFold|r19662]] -- Process gamma ray spectrum folds
  - [[CAxis|r19778]] -- Spectrum axis coordinate transforms.
  - [[CGate|r19890]] -- SpecTcl gate classes
  - [[CGateContainer|r21474]] -- Pointer like class for Gates.
  - [[CGateObserver|r21582]] -- Observe changes in the gate dictionary.
  - [[CFit|r21667]] -- Base class for spectrum fitting subsystem.
  - [[Predefined CFit classes|r21930]] -- 3SpecTcl
  - [[CSpectrumFit|r22098]] -- Fit of spectrum channels.
  - [[CFitFactory|r22281]] -- Creating fit objects by name
  - [[CFitDictionary|r22586]] -- Fitting subsystem dictionary.
  - [[CEventSink|r22858]] -- Base class for event sink pipeline elements
  - [[CEventFilter|r22920]] -- Abstract base class for event filters.
  - [[Root tree building|r22961]] -- Classes to build root trees.
  - [[RootTreeSink|r23349]] -- Event sink that writes root trees.
  - [[RootEventProcessor|r23465]] -- Event processor to manage root event sinks
  - [[CPipelineManager|r23554]] -- v5.1+ Dynamic pipeline management
  - [[CPipelineEventProcessor|r23927]] -- Encapsulate an event processing pipeline as a processor.
- V. [[SpecTcl Displays|p23943]]
  - [[CDisplay|r23949]] -- Display interface base class
  - [[CNullDisplay|r24269]] -- Batch mode displayer
  - [[CXamine|r24282]] -- Displayer class for Xamine
  - [[Xamine Gates|r24515]] -- Represent gates in Xamine
  - [[XamineButton|r24847]] -- Describe a client button
  - [[CXamineButtonPrompt|r24993]] -- Base class for button prompter descriptions
  - [[CXamineNoPrompt|r25009]] -- Prompter that does not prompt
  - [[CXamineConfirmPrompt|r25021]] -- Prompt for confirmation
  - [[CXamineTextPrompt|r25034]] -- Prompt for a text string
  - [[CXamineSpectrumPrompt|r25046]] -- Prompt for a spectrum
  - [[CXamineFilePrompt|r25066]] -- Prompt for a filename.
  - [[CXaminePointsPrompt|r25078]] -- Prompt for points
  - [[CXamineEvent|r25093]] -- Encapsulate events from Xamine.
  - [[CButtonEvent|r25124]] -- Encapsulate button press events
  - [[CDisplayInterface|r25245]] -- Manages displayers
  - [[CDisplayCollection|r25366]] -- Maintain a named set of display objects.
  - [[CDisplayFactory|r25473]] -- Associate display creators with display type names
- VI. [[Callback based analysis framework.|p25567]]
  - [[CAnalysisEventProcessor|r25571]] -- Event processor for callback analysis.
  - [[CAnalysisBase|r25649]] -- Base class for callout objects
  - [[CAnalysisBase|r25751]] -- Base class for callout analyzers.

- **List of Examples**
- 1. [[evttclsh|r6788#AEN6889]]

---

|  |  |  |
| --- | --- | --- |
|  |  | Next |
|  |  | Introduction |
