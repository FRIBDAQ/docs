|  |  |  |
| --- | --- | --- |
| SpecTcl Programming Reference. |
| Prev |  | Next |


---

# <a name="AEN23554"></a>CPipelineManager

<a name="AEN23558"></a>## Name

CPipelineManager -- v5.1+ Dynamic pipeline management

<a name="AEN23561"></a>## Synopsis

```
#include <CPipelineManager.h>
#include <TCLAnalyzer.h>
#include <stdexcept>

class CPipelineManager {
  
public:

  typedef std::map <std::string, CTclAnalyzer::EventProcessingPipeline* >
                                                    MapEventProcessingPipeline;
  typedef std::map <std::string, CEventProcessor*>
                                                    MapEventProcessors;

public:
  static CPipelineManager* getInstance();
  
  void registerEventProcessor(const std::string& name, CEventProcessor* pProcessor);
  void createPipeline(const std::string& name);
  
  void appendEventProcessor(const std::string& pipeName, const std::string& evpName);
  void insertEventProcessor(
    const std::string& pipename, const std::string& evpname,
    CTclAnalyzer::EventProcessorIterator where
  );

  void removeEventProcessor(const std::string& pipename, const std::string& evpname);
  void removeEventProcessor(const std::string& pipename, CTclAnalyzer::EventProcessorIterator here);
  
  void setCurrentPipeline(const std::string& pipename);
  
  void clonePipeline(const std::string& from, const std::string& to);

  // inquiries:
  
  CTclAnalyzer::EventProcessingPipeline* getCurrentPipeline();
  std::string                            getCurrentPipelineName() const;
  std::vector<std::string>               getPipelineNames() const;
  std::vector<std::string>               getEventProcessorNames() const;
  std::vector<std::string>               getEventProcessorsInPipeline(const std::string& pipename) const;
  std::string                            lookupEventProcessor(const CEventProcessor* p) const;
  
  size_t pipelineCount() const;
  size_t eventProcessorCount() const;
  
  MapEventProcessingPipeline::const_iterator pipelineBegin() const;
  MapEventProcessingPipeline::const_iterator pipelineEnd() const;
  
  MapEventProcessors::const_iterator processorsBegin() const;
  MapEventProcessors::const_iterator processorsEnd() const;

};
        
```

<a name="AEN23563"></a>## DESCRIPTION

The `CPipelineManager` class is a singleton
            class.   As such it has a private construtor and a
            `getInstance` static method used to
            obtain a pointer to the single instance of the class.

`CPipelineManager` along with the
            **pman** command ensemble are used to provide
            support for dynamic event processing pipeline manipulation.
            Using this object you can register event processors, create
            and stock event processing pipelines as well as select an
            event processing pipeline for use by the analyzer.

<a name="AEN23571"></a>## METHODS



` static   CPipelineManager*  getInstance();`This method is used to obtain a pointer to the one
                        and only instance of a `CPipelineManager`
                        class.  The `CPipelineManager` class
                        constructor is private,
                        as is its destructor.  Thus, this
                        is the only way to obtain a `CPipelineManager`
                        instance.

`   void  registerEventProcessor(const  std::string&  name, CEventProcessor* pProcessor);`Makes an event processor instance available to the
                        pipeline manager. `name` is the
                        name that will be associated with the event processor.
                        `pProcessor` points to the instance
                        of the processor.  The event processor  lifetime must
                        be the lifetime of SpecTcl's run.

`name` must be unique amongst all
                        event processors registered with the pipeline manager.
                        If an event processor with the same `name`
                        has alread been registered,
                        this method will throw a `std::logic_error`
                        exception.

`   void  createPipeline(const  std::string&  name);`Creates a new event processing pipeline.  The pipeline
                        is created without any event processors
                        (see however `clonePipeline` below).
                        `name` is the name that will be used
                        to identify the pipeline and must be unique among
                        all event processing pipelines managed by the pipeline
                        manager.  If a processing pipeline with the same
                        `name` already exists,
                        a `std::logic_error`
                        exception is thrown.

`   void appendEventProcessor(const  std::string&  pipeName , const  std::string&  evpName);`Appends an event processor to the set of event processors
                        in an event processing pipeline.
                        `pipeName` is the name of an
                        event processing pipeline that must already have been
                        made (note that when the pipeline manager is created,
                        it defines a pipeline named default).
                        `evpName` is the name of an event
                        processor that was registered with the pipeline manager.

If `pipeName` is not the name
                        of a pipeline or `evpName` is
                        not the name of an event processor, a
                        `std::logic_error` exception
                        is thrown.

`   void  insertEventProcessor(const  std::string&  pipename, const  std::string&  evpname, CTclAnalyzer::EventProcessorIterator  where);`Inserts an event processor in an arbitrary position
                        in an event processing pipeline.  This is deliberately
                        difficult.  `pipename`
                        is the name of an event processing pipeline that
                        already exists.  If it does not exist
                        a `std::logic_error` exception
                        is thrown.

`evpname` is the name of the
                        event processor to insert.  This event processor
                        instance must already have been registered or
                        a `std::logic_error` exception
                        is thrown.

`where` is an iterator into the
                        event processsing pipeline that specifies where the
                        where the processor while be inserted.  The processor
                        will be inserted after the `where`
                        iterator, unless it's an end iterator in which case
                        behavior is identical to `appendEventProcessor`

This method is discouraged and intentioally difficult to use.
                        To use it you'd need to obtain a pointer to an event processing
                        pipeline (either by getting the current one if that's what
                        you want to operate on or by iterating over the set of
                        pipelines).  Next you'd have to iterate over the pipeline
                        to obtain the insertion iterator.

`   void  removeEventProcessor(const  std::string&  pipename,  const  std::string&  evpname);`Removes the event processor named `evpname`
                        from the event processing pipeline named
                        `pipename`.  This is the preferred
                        way to remove an event processor from an processing
                        pipeline.

If `pipename` is not the  name
                        of an event proessing pipeline a
                        `std::logic_error` exception
                        is thrown.  If `evpname` is not
                        the name of an event processor that's in
                        `pipename`, a
                        `std::logic_error` exception
                        is thrown.

`   void  removeEventProcessor(const  std::string&  pipename, CTclAnalyzer::EventProcessorIterator  here);`Removes the event processor "pointed to" by the
                        iterator `here` from the
                        event processing pipeline named `pipename`.

If `pipename` is not the name of an
                        event processing pipeline, a
                        `std::logic_error` exception
                        is thrown.  Note that `here` must
                        be an iterator into the pipeline named by
                        `here` or else the results are
                        not defined.

`   void  setCurrentPipeline(const  std::string&  pipename);`Makes the pipeline named `pipename`
                        the current analysis pipeline. Beginning with the
                        next event, the analyzer will use this pipeline
                        to turn events into parameters.

If `pipename` is not an
                        analysis pipeline, a
                        `std::logic_error` exception is
                        thrown.

`    void  clonePipeline(const  std::string&  from, const  std::string&  to);`Creates a clone of the processing pipeline named
                        `from` named `to`.
                        The `to` pipeline will have all of
                        the event processors `from` has
                        (in the same order) and starts life off identical
                        to `from` in every way.

If `from` is not the name of
                        an event processing pipeline, a
                        `std::logic_error` exception
                        is thrown.  If `to` is already
                        the name of an event processing pipeline, a
                        `std::logic_error` exception
                        is thrown.

`   CTclAnalyzer::EventProcessingPipeline*  getCurrentPipeline();`Returns a pointer to the current event processing
                        pipeline.

`  const std::string getCurrentPipelineName();`Returns the name of the current event processing pipeline.

`  const std::vector<std::string>  getPipelineNames();`Returns a vector containing the names of the
                        event processing pipelines that have been defined.

`  const std::vector<std::string> getEventProcessorNames();`Returns the names of all of the event processors that
                        have been registered.

`  const std::vector<std::string> getEventProcessorsInPipeline(const  std::string&  pipename);`Returns a vector containing the names of event processors
                        in the pipeline named `pipename`.
                        The elements of the vector are the same as the
                        order of the corresponding event processors in the
                        pipeline.  If `pipename` is not
                        an event processing pipeline, a
                        `std::logic_error` exception
                        will be thrown.

`  const std::string   lookupEventProcessor(const  CEventProcessor*  p);`Given a pointer to an event processor that is registered
                        with the pipeline manager, returns the name under which
                        the processor was registered.  If there is no corresponding
                        event processor, a
                        `std::logic_error` exception is
                        thrown.

`  const size_t  pipelineCount();`Returns the number of event processing pipelines that
                        are defined.  Note that the
                        default pipeline always exists so
                        this is going to be no less than 1.

`  const size_t  eventProcessorCount();`Returns the number of event processors that have been
                        registered with the pipeline manager.

`  const MapEventProcessingPipeline::const_iterator  pipelineBegin();`, `  const MapEventProcessingPipeline::const_iterator  pipelineEnd();`Support iteration through the collection that contains
                        the event processing pipelines. See
                        DATA TYPES for a description of the
                        MapEventProcessingPipeline data type.
                        const_iterator implies the creation of a
                        pointer like object whose target is read-only.

`pipelineBegin` produces a
                        pointer-like object to the first element of the
                        collection.  `pipelineEnd`
                        produces a pointer like object just off the end
                        of the collection.  If an iterator is incremented and the
                        result is the return value from `pipelineEnd`,
                        iteration must be terminated.   Note that any additions to the
                        pipeline colletion invalidate any and all iterators into it.

`  const MapEventProcessors::const_iterator  processorsBegin() ();`, `  const MapEventProcessors::const_iterator  processorsEnd() ();`Supports iteration through the collection that
                        contains registered event processors.
                        `processorsBegin` returns a
                        pointer-like object to the beginning of the collection
                        and `processorsEnd` 'points'
                        just past the end of the collection.

See DATA TYPES below for more
                        information on what these iterators point at.

<a name="AEN23909"></a>## DATA TYPES

The `CPipelneManager` singleton exports
            data types for the containers that hold pipelines and event processors.
            The containser themselves are only accessible via constant
            iterators, however you need to know what those iterators 'point' to
            in order to use them.



CPipelineManager::MapEventProcessingPipelineThis is an `std::map` whose
                        contents are pointers to event processing pipelines
                        and whose keys are the names of those pipelines.
                        An iterator into this container will therefore look
                        like a pointer to
                        `std::pair<std::string, CTclAnalyzer::EventProcessingPipeline*>`.

CPipelineManager::MapEventProcessorsThis container is a map whose contents are pointers to
                        event processor instances and whose keys are the names under which
                        those instances were registered.  An iterator into this
                        container will threrefore look like a pointer to
                        `std::pair<std::string, CEventProcessor*>`.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| RootEventProcessor | Up | CPipelineEventProcessor |
