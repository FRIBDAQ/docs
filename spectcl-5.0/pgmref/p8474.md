|  |  |  |
| --- | --- | --- |
| SpecTcl Programming Reference. |
| Prev |  | Next |


---

<a name="AEN8474"></a># IV. Core SpecTcl classes

<a name="AEN8476"></a># Core SpecTcl classes

This part describes the core SpecTcl classes.  These  classes
                are those which can either be used by extensions to do their work
                or provide hooks for extensions written by users.

**Table of Contents**[[r8479]] -- Create factories that don't have hard-coded creationals.[[r8591]] -- Abstract base class convering events to parameters[[r8783]] -- Event processor for event built data.[[r8892]] -- Base Application class[[r9514]] -- SpecTcl histogramming core[[r10265]] -- Describe dictionaries used by SpecTcl[[r10876]] -- Analyzer base class and classic analyzer[[r11278]] -- Analyzer integrated with Tcl supporting pipeline[[r11832]] -- Base class for SpecTcl buffer decoders[[r12116]] -- Decode fixed sized event buffers from NSCLDAQ-7.x/8.x[[r12276]] -- Decode NSCLDAQ 7.x/8.x buffers bigger than 128Kbytes.[[r12440]] -- Decode data from ring buffers[[r12803]] -- ABC for4 ring buffer format helpers[[r12984]] -- Base class for items with names and ids.[[r13065]] -- Parameter definition.[[r13256]] -- Destination for decoded event data.[[r13409]] -- Classes implementing SpecTcl spectra[[r15613]] -- Process gamma ray spectrum folds[[r15729]] -- Spectrum axis coordinate transforms.[[r15841]] -- SpecTcl gate classes[[r17425]] -- Pointer like class for Gates.[[r17533]] -- Observe changes in the gate dictionary.[[r17618]] -- Base class for spectrum fitting subsystem.[[r17881]] -- 3SpecTcl[[r18049]] -- Fit of spectrum channels.[[r18232]] -- Creating fit objects by name[[r18537]] -- Fitting subsystem dictionary.[[r18809]] -- Base class for event sink pipeline elements[[r18871]] -- Abstract base class for event filters.[[r19167]] -- Filter with output conditionalized on a gate check.[[r19273]] -- Abstract base class for filter output streamers.[[r19381]] -- Filter output stage for writing Xdr filters.[[r19505]] -- Create filter output stages for
            `CFilterOutputStageFactory`[[r19567]] -- Create filter output stage objects.[[r19634]] -- 
            Create `CXrFilterOutputStage` objects
        [[r19648]] -- 
            Decodes events from a filter file into parameters.
        [[r19662]] -- Process gamma ray spectrum folds[[r19778]] -- Spectrum axis coordinate transforms.[[r19890]] -- SpecTcl gate classes[[r21474]] -- Pointer like class for Gates.[[r21582]] -- Observe changes in the gate dictionary.[[r21667]] -- Base class for spectrum fitting subsystem.[[r21930]] -- 3SpecTcl[[r22098]] -- Fit of spectrum channels.[[r22281]] -- Creating fit objects by name[[r22586]] -- Fitting subsystem dictionary.[[r22858]] -- Base class for event sink pipeline elements[[r22920]] -- Abstract base class for event filters.[[r22961]] -- Classes to build root trees.[[r23349]] -- Event sink that writes root trees.[[r23465]] -- Event processor to manage root event sinks[[r23554]] -- v5.1+ Dynamic pipeline management[[r23927]] -- Encapsulate an event processing pipeline as a processor.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CTCLPackagedObjectProcessor |  | Extensible Factories |
