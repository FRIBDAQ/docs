|  |  |  |
| --- | --- | --- |
| SpecTcl Programming Reference. |
| Prev |  | Next |


---

# <a name="AEN8783"></a>CEventBuilderEventProcessor

<a name="AEN8787"></a>## Name

CEventBuilderEventProcessor -- Event processor for event built data.

<a name="AEN8790"></a>## Synopsis

```
class CEventBuilderEventProcessor : public CEventProcessor
{
public:
    CEventBuilderEventProcessor(double clockMHz, std::string baseName);
    void addEventProcessor(unsigned sourceId, CEventProcessor& processor);
};

                
```

<a name="AEN8792"></a>## DESCRIPTION

Increasingly, experiments are composed of several
                    detector systems.  Each detector system has its own
                    independent data acquisition system.  These systems
                    run synchronized clocks that provide a timestamp for
                    each event fragment they produce.
                    An event builder is then used to combine
                    event fragments into events that contains fragments that
                    are coincident in time.

The `CEventBuilderEventProcessor`
                    is provided to simplify the unpacking of these events into
                    a base set of raw parameters.  It allows the registration
                    of event processors to handle each data source that can
                    produce event fragments.  For each event, control is dispatched
                    to the appropriate set of event processors.

<a name="AEN8797"></a>## METHODS

Naturally, the event processor methods are implemented by
                    this event processor.  For non physics events, each registered
                    event processor is called.  For `operator()`,
                    the event processor iterates over the fragments in each event
                    extracting the source id and body of the fragment.
                    The appropriate event processors are then dispatched to with
                    their `pEvent` pointing at that fragment's
                    body.

Thus, if you have an event processor which can unpack
                    data from a system in standalone  mode, you can register
                    that event processor to use it with event built data that
                    may contain fragments from that system.



`  CEventBuilderEventProcessor(double  clockMHz, std::string  baseName);`The constructor is parameterized.
                                `clockMHz` must be the
                                frequency of the timestamp clock in MHz.
                                This is used to produce a parameter that is
                                the run time in seconds.

The event produces several parameters of its own.
                                The `baseName` parameter
                                allows some control over the names of those parameters.
                                Specifically, each parameter name will be preceded by
                                the `baseName` and a
                                ..

Thus a `baseName` parameter
                                of diagnostics will
                                produce a parameter that is the run time in
                                seconds at which an event occured named
                                diagnostis.run_time.

See PARAMETERS below
                                for information about the set of parameters
                                this event processor produces.

`   void  addEventProcessor(unsigned  sourceId, CEventProcessor&  processor);`Adds an event prrocessor; `processor`
                                to process events from the specifice source;
                                `sourceId`.  Note that
                                each source can only have one event processor,
                                the last one registered for the source.

There is, however nothing to stop you from having
                                additional event processors registered in the
                                event processing pipeline after (or before for
                                that matter) the instance of
                                `CEventBuilderEventProcessor`./

There's also nothing to stop you from building event
                                processors that, themselves manage a pipeline of processors
                                if you need to have several event processors associated
                                with analyzing data from a specific event source.
                                Too much of this, however should make you  question the
                                organization of and or your processing of it.

<a name="AEN8847"></a>## PARAMETERS

This event processor creates severa parameters that are
                    useful in creating diagnostic spectra that are  typical
                    of a system using event built data.  In this section,
                    we will give the part of the parameter name that follows
                    the `basName` and following
                    . rather than doing something clumsy
                    to attempt to capture the entire parameter name pattern.

The parameters we produce are divided into a set of
                    fixed parameters and a set of parameters that depend on the
                    event processors registered with us.

The fixed set of parameters are:



sourcesThe number of sources present in the event.

unrecognized_sourceThe number of fragments that had source ids
                                    for which there was no registered event
                                    processor.

event_noThe event number numbered from zero.
                                    Note that with Xamine, channel 0
                                    of a histogram represents
                                    the underflow counters for the Root histogram.

run_timeThe number of seconds into the run corresponding
                                    to the timestamp of the first fragment in the
                                    event.


The following parameters depend on the set of sources
                    registered:



sid_presentThis is 1 if  a fragment from
                                source sid is present.  It is undefined if not.
                                For example, for source id 2, a parameter named
                                2_present will be created.

tdiffsThe subtree tdiffs will be
                                created.   Parameters in that subtree will
                                contain time differences between all ordered pairs
                                of fragment source ids.  For example, if I have source Ids
                                1, 2, and 3 registered in that order, the parameters
                                
                                tdiffs.1-2,
                                tdiffs.2-3 and
                                tdiffs.1-3 will be created.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CEventProcessor | Up | CTclGrammerApp |
