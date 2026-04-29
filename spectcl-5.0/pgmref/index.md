<a name="AEN1"></a># <a name="AEN2"></a>SpecTcl Programming Reference.

### <a name="AEN4"></a>Ron Fox


---

- **Table of Contents**
- 1. [Introduction](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/c13.md)
- I. [SpecTclAPI class](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/p31.md)
  - 2. [SpecTcl](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/c33.md)
  - [SpecTcl](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r37.md) -- API Singleton class.
- II. [Tree Parameter, Tree Variable API](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/p2375.md)
  - 3. [Tree parameter, tree variable API](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/c2377.md)
  - [CTreeParameter](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r2386.md) -- Parameter object 'independent' of rEvent
  - [CTreeParameterArray](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r3194.md) -- Arrays of tree parameters
  - [CTreeVariable](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r3671.md) -- Access to Tcl variables with metadata
  - [CTreeVariableProperites](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r4061.md) -- Shared properties of CTreeVariable
  - [CTreeVariableArray](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r4238.md) -- Container for an array of tree variables.
- III. [Tcl++ classes](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/p4402.md)
  - 4. [Tcl++ classes](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/c4404.md)
  - [CTCLInterpreter](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r4430.md) -- 
              Encapsulate a Tcl interpreter.
  - [CTCLInterpreterObject](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r4666.md) -- 
              Base class for objects that are associated with a Tcl Interpreter.
  - [CTCLResult](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r4745.md) -- 
              Provide an object oriented interace to the Tcl interpreter result.
  - [CTCLException](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r4856.md) -- 
              Class for reporting exceptional conditions in Tcl applications
              via the C++ try/catch mechanism.
  - [CTCLObjectProcessor](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r4999.md) -- 
              Abstract base class to encapsulate the Tcl object command interface exposed by
              `Tcl_CreateObjCommand`.
  - [CTCLProcessor](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r5114.md) -- 
              Provide `argc`, `argv`
              extension commands to Tcl.
  - [CTCLCompatibiltyProcessor](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r5304.md) -- 
              Adaptor between `CTCLOjbectProcessor`
              and `CTCLProcessor`.
  - [CTCLCommandPackage](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r5371.md) -- 
              Group several related Tcl command extensions and common services they
              may require together.
  - [CTCLPackagedCommand](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r5476.md) -- 
              Base class for a command that lives in a `CTCLCommandPackage`
  - [CTCLVariable](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r5537.md) -- 
              Encapsulate Tcl interpreter variables.
  - [CTCLApplication 3](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r5733.md) -- 
              Base class for TCL/Tk applications.
  - [CTCLHashTable](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r5780.md) -- 
              Object oriented interface to Tcl's hash table functions.
  - [CTCLHashTableItem](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r5911.md) -- 
              Encapsulation of an entry in a Tcl Hash table as encapsulated
              in `CTCLHashTable`
  - [CTCLHashTableIterator](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r5979.md) -- 
              Iterator for visiting all elements of a `CTCLHashTable`
  - [CTCLString](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r6075.md) -- 
              Provide a wrapper for the Tcl_DString data type
              and its API
  - [CTCLList](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r6292.md) -- 
              Provide access to Tcl List parsing.
  - [CTCLChannel](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r6401.md) -- 
              Provide a C++ abstraction wrapper for Tcl Channels.
  - [CTCLFileHandler](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r6571.md) -- 
              Base class for building object oriented Tcl File event handlers.
  - [CTCLIdleProcess](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r6657.md) -- 
              Allows the establishment of an executable object that
              can be scheduled to be invoked when the Tcl/Tk intperpreter
              has no events that require processing.
  - [CTCLTimer](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r6718.md) -- 
              Abstract base class for C++ objects attached to timer events.
  - [CTCLLiveEventLoop](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r6788.md) -- Run Tcl with event loop.
  - [CTCLChannelCommander](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r6892.md) -- Accept commands on a Tcl channel from the event loop.
  - [CTCLStdioCommander](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r7104.md) -- Event driven command input on stdin/stdout
  - [CTCLServer](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r7168.md) -- Listener for a Tcl server.
  - [CTCLTcpServerInstance](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r7296.md) -- Channel commander that is a server instance for `CTCLServer`
  - [CItemConfiguration](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r7369.md) -- Hold a configuration
  - [CConfigurableObject](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r8092.md) -- Base class for objects tht have a configuration.
  - [CTCLObjectPackage](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r8312.md) -- Provide common functionality for a set of
                  related commands.
  - [CTCLPackagedObjectProcessor](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r8374.md) -- Base class for commands living in a
                      `CTCLObjectPackage`
- IV. [Core SpecTcl classes](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/p8474.md)
  - [Extensible Factories](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r8479.md) -- Create factories that don't have hard-coded creationals.
  - [CEventProcessor](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r8591.md) -- Abstract base class convering events to parameters
  - [CEventBuilderEventProcessor](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r8783.md) -- Event processor for event built data.
  - [CTclGrammerApp](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r8892.md) -- Base Application class
  - [CHistogrammer](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r9514.md) -- SpecTcl histogramming core
  - [Dictionaries](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r10265.md) -- Describe dictionaries used by SpecTcl
  - [CAnalyzer](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r10876.md) -- Analyzer base class and classic analyzer
  - [CTclAnalyzer](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r11278.md) -- Analyzer integrated with Tcl supporting pipeline
  - [CBufferDecoder](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r11832.md) -- Base class for SpecTcl buffer decoders
  - [CNSCLBufferDecoder](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r12116.md) -- Decode fixed sized event buffers from NSCLDAQ-7.x/8.x
  - [CNSCLJumboBufferDecoder](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r12276.md) -- Decode NSCLDAQ 7.x/8.x buffers bigger than 128Kbytes.
  - [CRingBufferDecoder](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r12440.md) -- Decode data from ring buffers
  - [CRingFormatHelper](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r12803.md) -- ABC for4 ring buffer format helpers
  - [CNamedItem](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r12984.md) -- Base class for items with names and ids.
  - [CParameter](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r13065.md) -- Parameter definition.
  - [CEvent](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r13256.md) -- Destination for decoded event data.
  - [CSpectrum](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r13409.md) -- Classes implementing SpecTcl spectra
  - [CFold](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r15613.md) -- Process gamma ray spectrum folds
  - [CAxis](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r15729.md) -- Spectrum axis coordinate transforms.
  - [CGate](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r15841.md) -- SpecTcl gate classes
  - [CGateContainer](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r17425.md) -- Pointer like class for Gates.
  - [CGateObserver](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r17533.md) -- Observe changes in the gate dictionary.
  - [CFit](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r17618.md) -- Base class for spectrum fitting subsystem.
  - [Predefined CFit classes](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r17881.md) -- 3SpecTcl
  - [CSpectrumFit](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r18049.md) -- Fit of spectrum channels.
  - [CFitFactory](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r18232.md) -- Creating fit objects by name
  - [CFitDictionary](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r18537.md) -- Fitting subsystem dictionary.
  - [CEventSink](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r18809.md) -- Base class for event sink pipeline elements
  - [CEventFilter](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r18871.md) -- Abstract base class for event filters.
  - [CGatedEventFilter](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r19167.md) -- Filter with output conditionalized on a gate check.
  - [CFilterOutputStage](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r19273.md) -- Abstract base class for filter output streamers.
  - [CXdrFilterOutputStage](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r19381.md) -- Filter output stage for writing Xdr filters.
  - [CFilterOutputStageCreator](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r19505.md) -- Create filter output stages for
              `CFilterOutputStageFactory`
  - [CFilterOutputStageFactory](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r19567.md) -- Create filter output stage objects.
  - [CXdrFilterOutputStageCreator](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r19634.md) -- 
              Create `CXrFilterOutputStage` objects
  - [FilterEventProcessor](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r19648.md) -- 
              Decodes events from a filter file into parameters.
  - [CFold](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r19662.md) -- Process gamma ray spectrum folds
  - [CAxis](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r19778.md) -- Spectrum axis coordinate transforms.
  - [CGate](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r19890.md) -- SpecTcl gate classes
  - [CGateContainer](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r21474.md) -- Pointer like class for Gates.
  - [CGateObserver](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r21582.md) -- Observe changes in the gate dictionary.
  - [CFit](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r21667.md) -- Base class for spectrum fitting subsystem.
  - [Predefined CFit classes](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r21930.md) -- 3SpecTcl
  - [CSpectrumFit](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r22098.md) -- Fit of spectrum channels.
  - [CFitFactory](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r22281.md) -- Creating fit objects by name
  - [CFitDictionary](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r22586.md) -- Fitting subsystem dictionary.
  - [CEventSink](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r22858.md) -- Base class for event sink pipeline elements
  - [CEventFilter](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r22920.md) -- Abstract base class for event filters.
  - [Root tree building](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r22961.md) -- Classes to build root trees.
  - [RootTreeSink](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r23349.md) -- Event sink that writes root trees.
  - [RootEventProcessor](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r23465.md) -- Event processor to manage root event sinks
  - [CPipelineManager](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r23554.md) -- v5.1+ Dynamic pipeline management
  - [CPipelineEventProcessor](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r23927.md) -- Encapsulate an event processing pipeline as a processor.
- V. [SpecTcl Displays](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/p23943.md)
  - [CDisplay](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r23949.md) -- Display interface base class
  - [CNullDisplay](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r24269.md) -- Batch mode displayer
  - [CXamine](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r24282.md) -- Displayer class for Xamine
  - [Xamine Gates](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r24515.md) -- Represent gates in Xamine
  - [XamineButton](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r24847.md) -- Describe a client button
  - [CXamineButtonPrompt](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r24993.md) -- Base class for button prompter descriptions
  - [CXamineNoPrompt](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r25009.md) -- Prompter that does not prompt
  - [CXamineConfirmPrompt](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r25021.md) -- Prompt for confirmation
  - [CXamineTextPrompt](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r25034.md) -- Prompt for a text string
  - [CXamineSpectrumPrompt](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r25046.md) -- Prompt for a spectrum
  - [CXamineFilePrompt](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r25066.md) -- Prompt for a filename.
  - [CXaminePointsPrompt](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r25078.md) -- Prompt for points
  - [CXamineEvent](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r25093.md) -- Encapsulate events from Xamine.
  - [CButtonEvent](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r25124.md) -- Encapsulate button press events
  - [CDisplayInterface](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r25245.md) -- Manages displayers
  - [CDisplayCollection](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r25366.md) -- Maintain a named set of display objects.
  - [CDisplayFactory](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r25473.md) -- Associate display creators with display type names
- VI. [Callback based analysis framework.](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/p25567.md)
  - [CAnalysisEventProcessor](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r25571.md) -- Event processor for callback analysis.
  - [CAnalysisBase](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r25649.md) -- Base class for callout objects
  - [CAnalysisBase](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r25751.md) -- Base class for callout analyzers.

- **List of Examples**
- 1. [evttclsh](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/pgmref/r6788.md#AEN6889)

---

|  |  |  |
| --- | --- | --- |
|  |  | Next |
|  |  | Introduction |
