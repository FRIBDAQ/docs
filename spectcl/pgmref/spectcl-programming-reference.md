<a name="AEN1"></a># <a name="AEN2"></a>SpecTcl Programming Reference.

### <a name="AEN4"></a>Ron Fox


---

**Table of Contents**1. [[c13]]I. [[p31]]2. [[c33]][[r37]] -- API Singleton class.II. [[p2427]]3. [[c2429]][[r2438]] -- Parameter object 'independent' of rEvent[[r3246]] -- Arrays of tree parameters[[r3723]] -- Access to Tcl variables with metadata[[r4113]] -- Shared properties of CTreeVariable[[r4290]] -- Container for an array of tree variables.III. [[p4454]]4. [[c4456]][[r4482]] -- 
            Encapsulate a Tcl interpreter.
        [[r4718]] -- 
            Base class for objects that are associated with a Tcl Interpreter.
        [[r4797]] -- 
            Provide an object oriented interace to the Tcl interpreter result.
        [[r4908]] -- 
            Class for reporting exceptional conditions in Tcl applications
            via the C++ try/catch mechanism.
        [[r5051]] -- 
            Abstract base class to encapsulate the Tcl object command interface exposed by
            `Tcl_CreateObjCommand`.
        [[r5166]] -- 
            Provide `argc`, `argv`
            extension commands to Tcl.
        [[r5356]] -- 
            Adaptor between `CTCLOjbectProcessor`
            and `CTCLProcessor`.
        [[r5423]] -- 
            Group several related Tcl command extensions and common services they
            may require together.
        [[r5528]] -- 
            Base class for a command that lives in a `CTCLCommandPackage`
[[r5589]] -- 
            Encapsulate Tcl interpreter variables.
        [[r5785]] -- 
            Base class for TCL/Tk applications.
        [[r5832]] -- 
            Object oriented interface to Tcl's hash table functions.
        [[r5963]] -- 
            Encapsulation of an entry in a Tcl Hash table as encapsulated
            in `CTCLHashTable`
[[r6031]] -- 
            Iterator for visiting all elements of a `CTCLHashTable`
[[r6127]] -- 
            Provide a wrapper for the Tcl_DString data type
            and its API
        [[r6344]] -- 
            Provide access to Tcl List parsing.
        [[r6453]] -- 
            Provide a C++ abstraction wrapper for Tcl Channels.
        [[r6623]] -- 
            Base class for building object oriented Tcl File event handlers.
        [[r6709]] -- 
            Allows the establishment of an executable object that
            can be scheduled to be invoked when the Tcl/Tk intperpreter
            has no events that require processing.
        [[r6770]] -- 
            Abstract base class for C++ objects attached to timer events.
        [[r6840]] -- Run Tcl with event loop.[[r6944]] -- Accept commands on a Tcl channel from the event loop.[[r7156]] -- Event driven command input on stdin/stdout[[r7220]] -- Listener for a Tcl server.[[r7348]] -- Channel commander that is a server instance for `CTCLServer`[[r7421]] -- Hold a configuration[[r8144]] -- Base class for objects tht have a configuration.[[r8364]] -- Provide common functionality for a set of
                related commands.[[r8426]] -- Base class for commands living in a
                    `CTCLObjectPackage`
IV. [[p8526]][[r8531]] -- Create factories that don't have hard-coded creationals.[[r8643]] -- Abstract base class convering events to parameters[[r8835]] -- Event processor for event built data.[[r8944]] -- Base Application class[[r9566]] -- SpecTcl histogramming core[[r10317]] -- Describe dictionaries used by SpecTcl[[r10928]] -- Analyzer base class and classic analyzer[[r11330]] -- Analyzer integrated with Tcl supporting pipeline[[r11884]] -- Base class for SpecTcl buffer decoders[[r12168]] -- Decode fixed sized event buffers from NSCLDAQ-7.x/8.x[[r12328]] -- Decode NSCLDAQ 7.x/8.x buffers bigger than 128Kbytes.[[r12492]] -- Decode data from ring buffers[[r12855]] -- ABC for4 ring buffer format helpers[[r13036]] -- Base class for items with names and ids.[[r13117]] -- Parameter definition.[[r13308]] -- Destination for decoded event data.[[r13461]] -- Classes implementing SpecTcl spectra[[r15665]] -- Process gamma ray spectrum folds[[r15781]] -- Spectrum axis coordinate transforms.[[r15893]] -- SpecTcl gate classes[[r17477]] -- Pointer like class for Gates.[[r17585]] -- Observe changes in the gate dictionary.[[r17670]] -- Base class for spectrum fitting subsystem.[[r17933]] -- 3SpecTcl[[r18101]] -- Fit of spectrum channels.[[r18284]] -- Creating fit objects by name[[r18589]] -- Fitting subsystem dictionary.[[r18861]] -- Base class for event sink pipeline elements[[r18923]] -- Abstract base class for event filters.[[r19219]] -- Filter with output conditionalized on a gate check.[[r19325]] -- Abstract base class for filter output streamers.[[r19433]] -- Container for waveforms[[r19570]] -- Singleton that holds SpecTcl's known waveforms[[r19676]] -- Filter output stage for writing Xdr filters.[[r19800]] -- Create filter output stages for
            `CFilterOutputStageFactory`[[r19862]] -- Create filter output stage objects.[[r19929]] -- 
            Create `CXrFilterOutputStage` objects
        [[r19943]] -- 
            Decodes events from a filter file into parameters.
        [[r19957]] -- Process gamma ray spectrum folds[[r20073]] -- Spectrum axis coordinate transforms.[[r20185]] -- SpecTcl gate classes[[r21769]] -- Pointer like class for Gates.[[r21877]] -- Observe changes in the gate dictionary.[[r21962]] -- Base class for spectrum fitting subsystem.[[r22225]] -- 3SpecTcl[[r22393]] -- Fit of spectrum channels.[[r22576]] -- Creating fit objects by name[[r22881]] -- Fitting subsystem dictionary.[[r23153]] -- Base class for event sink pipeline elements[[r23215]] -- Abstract base class for event filters.[[r23256]] -- Classes to build root trees.[[r23644]] -- Event sink that writes root trees.[[r23760]] -- Event processor to manage root event sinks[[r23849]] -- v5.1+ Dynamic pipeline management[[r24222]] -- Encapsulate an event processing pipeline as a processor.V. [[p24238]][[r24244]] -- Display interface base class[[r24564]] -- Batch mode displayer[[r24577]] -- Displayer class for Xamine[[r24810]] -- Represent gates in Xamine[[r25142]] -- Describe a client button[[r25288]] -- Base class for button prompter descriptions[[r25304]] -- Prompter that does not prompt[[r25316]] -- Prompt for confirmation[[r25329]] -- Prompt for a text string[[r25341]] -- Prompt for a spectrum[[r25361]] -- Prompt for a filename.[[r25373]] -- Prompt for points[[r25388]] -- Encapsulate events from Xamine.[[r25419]] -- Encapsulate button press events[[r25540]] -- Manages displayers[[r25661]] -- Maintain a named set of display objects.[[r25768]] -- Associate display creators with display type namesVI. [[p25862]][[r25866]] -- Event processor for callback analysis.[[r25944]] -- Base class for callout objects[[r26046]] -- Base class for callout analyzers.

**List of Examples**1. [[r6840#AEN6941]]

---

|  |  |  |
| --- | --- | --- |
|  |  | Next |
|  |  | Introduction |
