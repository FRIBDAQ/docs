<a name="AEN1"></a># <a name="AEN2"></a>SpecTcl Programming Reference.

### <a name="AEN4"></a>Ron Fox


---

**Table of Contents**1. [[c13]]I. [[p31]]2. [[c33]][[r37]] -- API Singleton class.II. [[p2375]]3. [[c2377]][[r2386]] -- Parameter object 'independent' of rEvent[[r3194]] -- Arrays of tree parameters[[r3671]] -- Access to Tcl variables with metadata[[r4061]] -- Shared properties of CTreeVariable[[r4238]] -- Container for an array of tree variables.III. [[p4402]]4. [[c4404]][[r4430]] -- 
            Encapsulate a Tcl interpreter.
        [[r4666]] -- 
            Base class for objects that are associated with a Tcl Interpreter.
        [[r4745]] -- 
            Provide an object oriented interace to the Tcl interpreter result.
        [[r4856]] -- 
            Class for reporting exceptional conditions in Tcl applications
            via the C++ try/catch mechanism.
        [[r4999]] -- 
            Abstract base class to encapsulate the Tcl object command interface exposed by
            `Tcl_CreateObjCommand`.
        [[r5114]] -- 
            Provide `argc`, `argv`
            extension commands to Tcl.
        [[r5304]] -- 
            Adaptor between `CTCLOjbectProcessor`
            and `CTCLProcessor`.
        [[r5371]] -- 
            Group several related Tcl command extensions and common services they
            may require together.
        [[r5476]] -- 
            Base class for a command that lives in a `CTCLCommandPackage`
[[r5537]] -- 
            Encapsulate Tcl interpreter variables.
        [[r5733]] -- 
            Base class for TCL/Tk applications.
        [[r5780]] -- 
            Object oriented interface to Tcl's hash table functions.
        [[r5911]] -- 
            Encapsulation of an entry in a Tcl Hash table as encapsulated
            in `CTCLHashTable`
[[r5979]] -- 
            Iterator for visiting all elements of a `CTCLHashTable`
[[r6075]] -- 
            Provide a wrapper for the Tcl_DString data type
            and its API
        [[r6292]] -- 
            Provide access to Tcl List parsing.
        [[r6401]] -- 
            Provide a C++ abstraction wrapper for Tcl Channels.
        [[r6571]] -- 
            Base class for building object oriented Tcl File event handlers.
        [[r6657]] -- 
            Allows the establishment of an executable object that
            can be scheduled to be invoked when the Tcl/Tk intperpreter
            has no events that require processing.
        [[r6718]] -- 
            Abstract base class for C++ objects attached to timer events.
        [[r6788]] -- Run Tcl with event loop.[[r6892]] -- Accept commands on a Tcl channel from the event loop.[[r7104]] -- Event driven command input on stdin/stdout[[r7168]] -- Listener for a Tcl server.[[r7296]] -- Channel commander that is a server instance for `CTCLServer`[[r7369]] -- Hold a configuration[[r8092]] -- Base class for objects tht have a configuration.[[r8312]] -- Provide common functionality for a set of
                related commands.[[r8374]] -- Base class for commands living in a
                    `CTCLObjectPackage`
IV. [[p8474]][[r8479]] -- Create factories that don't have hard-coded creationals.[[r8591]] -- Abstract base class convering events to parameters[[r8783]] -- Event processor for event built data.[[r8892]] -- Base Application class[[r9514]] -- SpecTcl histogramming core[[r10265]] -- Describe dictionaries used by SpecTcl[[r10876]] -- Analyzer base class and classic analyzer[[r11278]] -- Analyzer integrated with Tcl supporting pipeline[[r11832]] -- Base class for SpecTcl buffer decoders[[r12116]] -- Decode fixed sized event buffers from NSCLDAQ-7.x/8.x[[r12276]] -- Decode NSCLDAQ 7.x/8.x buffers bigger than 128Kbytes.[[r12440]] -- Decode data from ring buffers[[r12803]] -- ABC for4 ring buffer format helpers[[r12984]] -- Base class for items with names and ids.[[r13065]] -- Parameter definition.[[r13256]] -- Destination for decoded event data.[[r13409]] -- Classes implementing SpecTcl spectra[[r15613]] -- Process gamma ray spectrum folds[[r15729]] -- Spectrum axis coordinate transforms.[[r15841]] -- SpecTcl gate classes[[r17425]] -- Pointer like class for Gates.[[r17533]] -- Observe changes in the gate dictionary.[[r17618]] -- Base class for spectrum fitting subsystem.[[r17881]] -- 3SpecTcl[[r18049]] -- Fit of spectrum channels.[[r18232]] -- Creating fit objects by name[[r18537]] -- Fitting subsystem dictionary.[[r18809]] -- Base class for event sink pipeline elements[[r18871]] -- Abstract base class for event filters.[[r19167]] -- Filter with output conditionalized on a gate check.[[r19273]] -- Abstract base class for filter output streamers.[[r19381]] -- Filter output stage for writing Xdr filters.[[r19505]] -- Create filter output stages for
            `CFilterOutputStageFactory`[[r19567]] -- Create filter output stage objects.[[r19634]] -- 
            Create `CXrFilterOutputStage` objects
        [[r19648]] -- 
            Decodes events from a filter file into parameters.
        [[r19662]] -- Process gamma ray spectrum folds[[r19778]] -- Spectrum axis coordinate transforms.[[r19890]] -- SpecTcl gate classes[[r21474]] -- Pointer like class for Gates.[[r21582]] -- Observe changes in the gate dictionary.[[r21667]] -- Base class for spectrum fitting subsystem.[[r21930]] -- 3SpecTcl[[r22098]] -- Fit of spectrum channels.[[r22281]] -- Creating fit objects by name[[r22586]] -- Fitting subsystem dictionary.[[r22858]] -- Base class for event sink pipeline elements[[r22920]] -- Abstract base class for event filters.[[r22961]] -- Classes to build root trees.[[r23349]] -- Event sink that writes root trees.[[r23465]] -- Event processor to manage root event sinks[[r23554]] -- v5.1+ Dynamic pipeline management[[r23927]] -- Encapsulate an event processing pipeline as a processor.V. [[p23943]][[r23949]] -- Display interface base class[[r24269]] -- Batch mode displayer[[r24282]] -- Displayer class for Xamine[[r24515]] -- Represent gates in Xamine[[r24847]] -- Describe a client button[[r24993]] -- Base class for button prompter descriptions[[r25009]] -- Prompter that does not prompt[[r25021]] -- Prompt for confirmation[[r25034]] -- Prompt for a text string[[r25046]] -- Prompt for a spectrum[[r25066]] -- Prompt for a filename.[[r25078]] -- Prompt for points[[r25093]] -- Encapsulate events from Xamine.[[r25124]] -- Encapsulate button press events[[r25245]] -- Manages displayers[[r25366]] -- Maintain a named set of display objects.[[r25473]] -- Associate display creators with display type namesVI. [[p25567]][[r25571]] -- Event processor for callback analysis.[[r25649]] -- Base class for callout objects[[r25751]] -- Base class for callout analyzers.

**List of Examples**1. [[r6788#AEN6889]]

---

|  |  |  |
| --- | --- | --- |
|  |  | Next |
|  |  | Introduction |
