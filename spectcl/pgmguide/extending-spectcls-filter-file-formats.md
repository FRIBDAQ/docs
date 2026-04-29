|  |  |  |
| --- | --- | --- |
| SpecTcl Programming Guide. |
| Prev |  | Next |


---

# <a name="chap.filterformat"></a>Chapter 8. 
        Extending SpecTcl's filter file formats

Filters are objects int he event sink pipeline that produce
        reduced data set output files.  Filters reduce data by a combination
        of selecting events and selecting a subset of parameters in each selected
        event.

Typically filtered data is self describing and, therefore, faster to analyze
        because parsing is simplified.  SpecTcl supports a native filter format
        based on the SUN XDR source independent data representation.  Data in
        XDR files can be decoded regardless of the byte ordering of the source
        and sink systems.

The filter formats supported by SpecTcl are extensible.  In fact,
        a plugin allows filtered data to be written in a format friendly to
        the CERN [ROOT](http://root.cern.ch) program.  (See
        [[c4069]]
        for information about SpecTcl plugins and how to write them).

In this chapter we will:



- Look at the classes and objects that make filter formats
                  extensible (
                  [[c2080#sec.filterformatobjects]]).
- Walk through writing an extension to the set of filter formats
                  supported by SpecTcl.
                  [[x2310]]

# <a name="sec.filterformatobjects"></a>8.1. Filter formatting objects.

Filters rely on a `CFilterOutputStage` object
            to actually output data to the filter file.  This is defined
            in the header CFilterOutpuStage.h.

`CFilterOutputStage` is a base class.  It
            defines the following interface:

<a name="AEN2102"></a>**Example 8-1. `CFilterOutputStage` class definition**

```
class CFilterOutputStage
{
public:

public:
  virtual void open(std::string filename) = 0;
  virtual void close() = 0;
  virtual void onAttach(CEventFilter& filter);
  virtual void DescribeEvent(std::vector<std::string> parameterNames,
			     std::vector<UInt_t>      parameterIds) =0;
  virtual void operator()(CEvent& event) = 0;
  virtual std::string  type() const = 0;
};
            
```

Since all of these methods are pure virtual, a new filter output
            stage  must provide all of them:



` virtual   = 0; void  open( std::string  filename);`This is called to open a filter file.
                        `filename` is the name of the file
                        to open.  The object must then maintain whatever is used
                        to write to the file (stream, file pointer, or file number)
                        internally until `close` is called.

The object is assured that future calls to
                        `DescribeEvent` and
                        `operator()` will need to refer
                        to the opened file.  The object is also assured that
                        neither of these will be called without a prior call
                        to `open`.

` virtual  = 0 void  close();`Called to close a filter file.  The file most
                        recently opened via `open`
                        should be closed.  Any resources associated with that
                        file can be released.  Any internally buffered events
                        should be flushed to the file prior to actually
                        closing it.

` virtual   void  onAttach( CEventFilter&  filter));`Called when the formatter is attached to a filter.  The
                        attached filter is the object that will be invoking the
                        methods of this object.   This has a default implementation
                        that does nothing.  Very frequently that's sufficient.

` virtual  = 0 void  DescribeEvent( std::vector<std::string> parameterNames,  std::vector<UInt_t> parameterIds);`Called just prior to recording data to the filter.
                        The method parameters describe the parameters to be
                        written. `parameterNames` is
                        a vector of the names of the parameters to be written
                        to the filter.  `parameterIds` are
                        the corresponding Ids (indices in the event array like
                        object).

Normally the filter output format objects should
                        write information to the output file that allows
                        a reader to determine which parameters are present and
                        how to unpack them from filter files.
                        `parameterIds` should usually
                        be retained to know which parameters in
                        an event array like object `operator()`
                        should write.

` virtual  = 0 void  operator()( CEvent&  event);`Called for every event that satisfies the filter's gate.
                        Its now up to the object to write the parameters the
                        filter cares about to the output file.  Note that prior
                        to this, the filter would have invoked
                        `DescribeEvent` and the
                        vector of indices into `event`
                        will have been passed to that method.

` virtual   const = 0 std::string   type();`Invoked to get a short textual string that specifies the
                        output type.

It's not enoubh to have a filter output stage.  The **filter**
            command ensemble must know about it and be able to instantiate it
            given a value for the **filter -format** command.
            This is done by registering a `CFilterOutputStageCreator`
            with a singleton `CFilterOutputStageFactory`.

The `CFilterOutputStageFactory` serves two
            purposes.  It provides the **filter** command
            with a list of formats and their descriptions for use in the
            help text.  It also, given a format name, produces the appropriate
            `CFilterOutputStage` object to attach to
            a filter to provide that format.

The `CFilterOutputStageCreator` is normally
            quite trivial:

<a name="AEN2209"></a>**Example 8-2. `CFilterOutputStageCreator` specification**

```
class CFilterOutputStageCreator
{
public:
  virtual CFilterOutputStage*  operator()(std::string type) = 0;
  virtual std::string document() const = 0;
  virtual CFilterOutputStageCreator* clone() = 0;
};
            
```



` virtual  =0 CFilterOutputStage*   operator()( std::string type);`If `type` is a formatter type the
                        concrete output creator can create, it will return a pointer
                        to a new, dyanmically  created `CFilterOutputStage`
                        object that outputs data in accordance to the requested
                        format `type`.

` virtual  const = 0 std::string  document();`Returns a documentation string that describes the types
                        created and their meaning.  This text is output by the
                        **filter** command as part of its help
                        text.  The XDR creator, for example, returns:
                        xdr        - NSCL XDR system independent filter file format.

` virtual  = 0 CFilterOutputStageCreator*  clone();`Returns a pointer to a dynamically created clone of
                        the object.  This provides an effectively virtual
                        copy construction.  Note, however, unlike copy
                        construction of temporaries, the caller will need
                        to explicitly **delete** the object
                        returned.

Creator objects are made known to the filter subsystem by
            registering them in the `CFilterOutputStageFactory`
            singleton object.  This class is defined in
            CFilterOutputStageFactory.h.  The key
            parts of that file look like this:

<a name="AEN2256"></a>**Example 8-3. `CFilterOutputStageFactory` definition**

```
class CFilterOutputStageFactory {

  
public:
  static CFilterOutputStageFactory& getInstance();
  
  CFilterOutputStage* create(std::string type) const;
  void                Register(CFilterOutputStageCreator& creator);
  std::string         document() const;
};

            
```



` static ;  CFilterOutputStageFactory&  getInstance();`This static method returns a reference to the singleton
                        object.  Once you have that object you can invoke
                        other, non static, methods on the singleton.

`  const CFilterOutputStage*  create( std::string  type);`Given a format type, this returns a pointer to a
                        dynamically created output stage object that can
                        be attached to a filter to produce an output file
                        of the type requested by the `type`
                        parameter.

This method is intended to be called by the
                        code that executes the
                        **filter -format** command.

`   void  Register( CFilterOutputStageCreator&  creator);`Adds a new creator, and hence a new format type to the
                        factory.  This is intended to be used by programmers
                        that write new filter output formats.

`  const std::string document();`This method aggregates all of the documentation
                        strings returned by all creators into a string
                        that documents all of the format types and their meanings.
                        The list of creators is visited and each visitor
                        contributes its documentation string to the result string.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Adding a CSV file format to spectrum read/write |  | Example filter formatter. |
