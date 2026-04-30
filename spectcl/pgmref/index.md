[← Tcl++ classes](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/c4456.md) | [Home](https://github.com/FRIBDAQ/docs/tree/main/Home.md) | [SpecTcl Displays →](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/p24238.md)

---

<a name="AEN1"></a># <a name="AEN2"></a>SpecTcl Programming Reference.

### <a name="AEN4"></a>Ron Fox


---

- **Table of Contents**
- 1. [Introduction](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/c13.md)
- I. [SpecTclAPI class](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/p31.md)
  - 2. [SpecTcl](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/c33.md)
  - [SpecTcl](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r37.md) -- API Singleton class.
- II. [Tree Parameter, Tree Variable API](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/p2427.md)
  - 3. [Tree parameter, tree variable API](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/c2429.md)
  - [CTreeParameter](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r2438.md) -- Parameter object 'independent' of rEvent
  - [CTreeParameterArray](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r3246.md) -- Arrays of tree parameters
  - [CTreeVariable](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r3723.md) -- Access to Tcl variables with metadata
  - [CTreeVariableProperites](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r4113.md) -- Shared properties of CTreeVariable
  - [CTreeVariableArray](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r4290.md) -- Container for an array of tree variables.
- III. [Tcl++ classes](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/p4454.md)
  - 4. [Tcl++ classes](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/c4456.md)
  - [CTCLInterpreter](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r4482.md) -- 
              Encapsulate a Tcl interpreter.
  - [CTCLInterpreterObject](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r4718.md) -- 
              Base class for objects that are associated with a Tcl Interpreter.
  - [CTCLResult](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r4797.md) -- 
              Provide an object oriented interace to the Tcl interpreter result.
  - [CTCLException](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r4908.md) -- 
              Class for reporting exceptional conditions in Tcl applications
              via the C++ try/catch mechanism.
  - [CTCLObjectProcessor](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r5051.md) -- 
              Abstract base class to encapsulate the Tcl object command interface exposed by
              `Tcl_CreateObjCommand`.
  - [CTCLProcessor](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r5166.md) -- 
              Provide `argc`, `argv`
              extension commands to Tcl.
  - [CTCLCompatibiltyProcessor](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r5356.md) -- 
              Adaptor between `CTCLOjbectProcessor`
              and `CTCLProcessor`.
  - [CTCLCommandPackage](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r5423.md) -- 
              Group several related Tcl command extensions and common services they
              may require together.
  - [CTCLPackagedCommand](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r5528.md) -- 
              Base class for a command that lives in a `CTCLCommandPackage`
  - [CTCLVariable](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r5589.md) -- 
              Encapsulate Tcl interpreter variables.
  - [CTCLApplication 3](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r5785.md) -- 
              Base class for TCL/Tk applications.
  - [CTCLHashTable](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r5832.md) -- 
              Object oriented interface to Tcl's hash table functions.
  - [CTCLHashTableItem](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r5963.md) -- 
              Encapsulation of an entry in a Tcl Hash table as encapsulated
              in `CTCLHashTable`
  - [CTCLHashTableIterator](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r6031.md) -- 
              Iterator for visiting all elements of a `CTCLHashTable`
  - [CTCLString](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r6127.md) -- 
              Provide a wrapper for the Tcl_DString data type
              and its API
  - [CTCLList](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r6344.md) -- 
              Provide access to Tcl List parsing.
  - [CTCLChannel](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r6453.md) -- 
              Provide a C++ abstraction wrapper for Tcl Channels.
  - [CTCLFileHandler](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r6623.md) -- 
              Base class for building object oriented Tcl File event handlers.
  - [CTCLIdleProcess](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r6709.md) -- 
              Allows the establishment of an executable object that
              can be scheduled to be invoked when the Tcl/Tk intperpreter
              has no events that require processing.
  - [CTCLTimer](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r6770.md) -- 
              Abstract base class for C++ objects attached to timer events.
  - [CTCLLiveEventLoop](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r6840.md) -- Run Tcl with event loop.
  - [CTCLChannelCommander](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r6944.md) -- Accept commands on a Tcl channel from the event loop.
  - [CTCLStdioCommander](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r7156.md) -- Event driven command input on stdin/stdout
  - [CTCLServer](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r7220.md) -- Listener for a Tcl server.
  - [CTCLTcpServerInstance](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r7348.md) -- Channel commander that is a server instance for `CTCLServer`
  - [CItemConfiguration](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r7421.md) -- Hold a configuration
  - [CConfigurableObject](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r8144.md) -- Base class for objects tht have a configuration.
  - [CTCLObjectPackage](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r8364.md) -- Provide common functionality for a set of
                  related commands.
  - [CTCLPackagedObjectProcessor](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r8426.md) -- Base class for commands living in a
                      `CTCLObjectPackage`
- IV. [Core SpecTcl classes](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/p8526.md)
  - [Extensible Factories](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r8531.md) -- Create factories that don't have hard-coded creationals.
  - [CEventProcessor](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r8643.md) -- Abstract base class convering events to parameters
  - [CEventBuilderEventProcessor](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r8835.md) -- Event processor for event built data.
  - [CTclGrammerApp](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r8944.md) -- Base Application class
  - [CHistogrammer](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r9566.md) -- SpecTcl histogramming core
  - [Dictionaries](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r10317.md) -- Describe dictionaries used by SpecTcl
  - [CAnalyzer](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r10928.md) -- Analyzer base class and classic analyzer
  - [CTclAnalyzer](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r11330.md) -- Analyzer integrated with Tcl supporting pipeline
  - [CBufferDecoder](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r11884.md) -- Base class for SpecTcl buffer decoders
  - [CNSCLBufferDecoder](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r12168.md) -- Decode fixed sized event buffers from NSCLDAQ-7.x/8.x
  - [CNSCLJumboBufferDecoder](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r12328.md) -- Decode NSCLDAQ 7.x/8.x buffers bigger than 128Kbytes.
  - [CRingBufferDecoder](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r12492.md) -- Decode data from ring buffers
  - [CRingFormatHelper](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r12855.md) -- ABC for4 ring buffer format helpers
  - [CNamedItem](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r13036.md) -- Base class for items with names and ids.
  - [CParameter](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r13117.md) -- Parameter definition.
  - [CEvent](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r13308.md) -- Destination for decoded event data.
  - [CSpectrum](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r13461.md) -- Classes implementing SpecTcl spectra
  - [CFold](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r15665.md) -- Process gamma ray spectrum folds
  - [CAxis](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r15781.md) -- Spectrum axis coordinate transforms.
  - [CGate](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r15893.md) -- SpecTcl gate classes
  - [CGateContainer](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r17477.md) -- Pointer like class for Gates.
  - [CGateObserver](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r17585.md) -- Observe changes in the gate dictionary.
  - [CFit](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r17670.md) -- Base class for spectrum fitting subsystem.
  - [Predefined CFit classes](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r17933.md) -- 3SpecTcl
  - [CSpectrumFit](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r18101.md) -- Fit of spectrum channels.
  - [CFitFactory](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r18284.md) -- Creating fit objects by name
  - [CFitDictionary](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r18589.md) -- Fitting subsystem dictionary.
  - [CEventSink](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r18861.md) -- Base class for event sink pipeline elements
  - [CEventFilter](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r18923.md) -- Abstract base class for event filters.
  - [CGatedEventFilter](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r19219.md) -- Filter with output conditionalized on a gate check.
  - [CFilterOutputStage](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r19325.md) -- Abstract base class for filter output streamers.
  - [CWaveform](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r19433.md) -- Container for waveforms
  - [CWaveformDictionary](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r19570.md) -- Singleton that holds SpecTcl's known waveforms
  - [CXdrFilterOutputStage](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r19676.md) -- Filter output stage for writing Xdr filters.
  - [CFilterOutputStageCreator](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r19800.md) -- Create filter output stages for
              `CFilterOutputStageFactory`
  - [CFilterOutputStageFactory](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r19862.md) -- Create filter output stage objects.
  - [CXdrFilterOutputStageCreator](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r19929.md) -- 
              Create `CXrFilterOutputStage` objects
  - [FilterEventProcessor](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r19943.md) -- 
              Decodes events from a filter file into parameters.
  - [CFold](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r19957.md) -- Process gamma ray spectrum folds
  - [CAxis](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r20073.md) -- Spectrum axis coordinate transforms.
  - [CGate](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r20185.md) -- SpecTcl gate classes
  - [CGateContainer](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r21769.md) -- Pointer like class for Gates.
  - [CGateObserver](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r21877.md) -- Observe changes in the gate dictionary.
  - [CFit](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r21962.md) -- Base class for spectrum fitting subsystem.
  - [Predefined CFit classes](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r22225.md) -- 3SpecTcl
  - [CSpectrumFit](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r22393.md) -- Fit of spectrum channels.
  - [CFitFactory](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r22576.md) -- Creating fit objects by name
  - [CFitDictionary](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r22881.md) -- Fitting subsystem dictionary.
  - [CEventSink](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r23153.md) -- Base class for event sink pipeline elements
  - [CEventFilter](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r23215.md) -- Abstract base class for event filters.
  - [Root tree building](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r23256.md) -- Classes to build root trees.
  - [RootTreeSink](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r23644.md) -- Event sink that writes root trees.
  - [RootEventProcessor](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r23760.md) -- Event processor to manage root event sinks
  - [CPipelineManager](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r23849.md) -- v5.1+ Dynamic pipeline management
  - [CPipelineEventProcessor](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r24222.md) -- Encapsulate an event processing pipeline as a processor.
- V. [SpecTcl Displays](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/p24238.md)
  - [CDisplay](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r24244.md) -- Display interface base class
  - [CNullDisplay](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r24564.md) -- Batch mode displayer
  - [CXamine](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r24577.md) -- Displayer class for Xamine
  - [Xamine Gates](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r24810.md) -- Represent gates in Xamine
  - [XamineButton](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r25142.md) -- Describe a client button
  - [CXamineButtonPrompt](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r25288.md) -- Base class for button prompter descriptions
  - [CXamineNoPrompt](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r25304.md) -- Prompter that does not prompt
  - [CXamineConfirmPrompt](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r25316.md) -- Prompt for confirmation
  - [CXamineTextPrompt](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r25329.md) -- Prompt for a text string
  - [CXamineSpectrumPrompt](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r25341.md) -- Prompt for a spectrum
  - [CXamineFilePrompt](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r25361.md) -- Prompt for a filename.
  - [CXaminePointsPrompt](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r25373.md) -- Prompt for points
  - [CXamineEvent](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r25388.md) -- Encapsulate events from Xamine.
  - [CButtonEvent](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r25419.md) -- Encapsulate button press events
  - [CDisplayInterface](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r25540.md) -- Manages displayers
  - [CDisplayCollection](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r25661.md) -- Maintain a named set of display objects.
  - [CDisplayFactory](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r25768.md) -- Associate display creators with display type names
- VI. [Callback based analysis framework.](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/p25862.md)
  - [CAnalysisEventProcessor](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r25866.md) -- Event processor for callback analysis.
  - [CAnalysisBase](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r25944.md) -- Base class for callout objects
  - [CAnalysisBase](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r26046.md) -- Base class for callout analyzers.

- **List of Examples**
- 1. [evttclsh](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/r6840.md#AEN6941)

---

---

[← Tcl++ classes](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/c4456.md) | [Home](https://github.com/FRIBDAQ/docs/tree/main/Home.md) | [SpecTcl Displays →](https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/p24238.md)
