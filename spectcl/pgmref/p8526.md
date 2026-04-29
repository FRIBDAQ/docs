|  |  |  |
| --- | --- | --- |
| SpecTcl Programming Reference. |
| Prev |  | Next |


---

<a name="AEN8526"></a># IV. Core SpecTcl classes

<a name="AEN8528"></a># Core SpecTcl classes

This part describes the core SpecTcl classes.  These  classes
                are those which can either be used by extensions to do their work
                or provide hooks for extensions written by users.

**Table of Contents**[[r8531]] -- Create factories that don't have hard-coded creationals.[[r8643]] -- Abstract base class convering events to parameters[[r8835]] -- Event processor for event built data.[[r8944]] -- Base Application class[[r9566]] -- SpecTcl histogramming core[[r10317]] -- Describe dictionaries used by SpecTcl[[r10928]] -- Analyzer base class and classic analyzer[[r11330]] -- Analyzer integrated with Tcl supporting pipeline[[r11884]] -- Base class for SpecTcl buffer decoders[[r12168]] -- Decode fixed sized event buffers from NSCLDAQ-7.x/8.x[[r12328]] -- Decode NSCLDAQ 7.x/8.x buffers bigger than 128Kbytes.[[r12492]] -- Decode data from ring buffers[[r12855]] -- ABC for4 ring buffer format helpers[[r13036]] -- Base class for items with names and ids.[[r13117]] -- Parameter definition.[[r13308]] -- Destination for decoded event data.[[r13461]] -- Classes implementing SpecTcl spectra[[r15665]] -- Process gamma ray spectrum folds[[r15781]] -- Spectrum axis coordinate transforms.[[r15893]] -- SpecTcl gate classes[[r17477]] -- Pointer like class for Gates.[[r17585]] -- Observe changes in the gate dictionary.[[r17670]] -- Base class for spectrum fitting subsystem.[[r17933]] -- 3SpecTcl[[r18101]] -- Fit of spectrum channels.[[r18284]] -- Creating fit objects by name[[r18589]] -- Fitting subsystem dictionary.[[r18861]] -- Base class for event sink pipeline elements[[r18923]] -- Abstract base class for event filters.[[r19219]] -- Filter with output conditionalized on a gate check.[[r19325]] -- Abstract base class for filter output streamers.[[r19433]] -- Container for waveforms[[r19570]] -- Singleton that holds SpecTcl's known waveforms[[r19676]] -- Filter output stage for writing Xdr filters.[[r19800]] -- Create filter output stages for
            `CFilterOutputStageFactory`[[r19862]] -- Create filter output stage objects.[[r19929]] -- 
            Create `CXrFilterOutputStage` objects
        [[r19943]] -- 
            Decodes events from a filter file into parameters.
        [[r19957]] -- Process gamma ray spectrum folds[[r20073]] -- Spectrum axis coordinate transforms.[[r20185]] -- SpecTcl gate classes[[r21769]] -- Pointer like class for Gates.[[r21877]] -- Observe changes in the gate dictionary.[[r21962]] -- Base class for spectrum fitting subsystem.[[r22225]] -- 3SpecTcl[[r22393]] -- Fit of spectrum channels.[[r22576]] -- Creating fit objects by name[[r22881]] -- Fitting subsystem dictionary.[[r23153]] -- Base class for event sink pipeline elements[[r23215]] -- Abstract base class for event filters.[[r23256]] -- Classes to build root trees.[[r23644]] -- Event sink that writes root trees.[[r23760]] -- Event processor to manage root event sinks[[r23849]] -- v5.1+ Dynamic pipeline management[[r24222]] -- Encapsulate an event processing pipeline as a processor.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CTCLPackagedObjectProcessor |  | Extensible Factories |
