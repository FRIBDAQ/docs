|  |  |  |
| --- | --- | --- |
| SpecTcl Programming Reference. |
| Prev |  | Next |


---

# <a name="AEN8892"></a>CTclGrammerApp

<a name="AEN8896"></a>## Name

CTclGrammerApp -- Base Application class

<a name="AEN8899"></a>## Synopsis

```
CTclGrammerApp
```

<a name="AEN8902"></a>## DESCRIPTION

This class is the base class of the SpecTcl application
                    class.  The standard SpecTcl skeleton provides a derivation
                    (`MySpecTclApp`) which has stubs for all
                    of the pure virtual methods.  Specialized derived classes
                    can do quite a bit more.

In general, to make a complete SpecTcl, you must write
                    a class derived from `CTclGrammerApp`,
                    instantiate it and assign a pointer to the global variable
                    `CTclGrammerApp::m_pInstance`.

While normally this sort of thing might be a singleton
                    pattern, our need to derive and use the *strategy pattern*
                    makes these gymnastics necessary.  For more on the
                    singleton pattern see:
                    [https://en.wikipedia.org/wiki/Singleton_pattern](https://en.wikipedia.org/wiki/Singleton_pattern).
                    For information on the strategy pattern, see:
                    [https://en.wikipedia.org/wiki/Strategy_pattern](https://en.wikipedia.org/wiki/Strategy_pattern).

<a name="AEN8913"></a>## METHODS

The methods for this class come in several categories.
                    Since this is an important base class, we'll be documenting
                    methods that include accessors and mutators for member data
                    as well as protected methods that may be of use in special
                    situations.

The first category of methods we'll document are accessors.
                    These are methods that allow read access to member data.
                    They are all public as external objects may want to
                    obtain the values of these variables as well as derived
                    classes:



`  const UInt_t  getDisplaySize();`SpecTcl places bulk spectrum data in a shared
                                memory region using the **sbind**
                                command.  This allows displayers running on the
                                same system as SpecTcl rapid access to these
                                data improving display rendering times.

The size of the shared memory region is determined
                                at startup (just after limit scripts are sourced).
                                This method returns the number of megabytes allocated
                                to this shared memory region.

Note that as for most computer applications
                                Mega means 1024*1024.

`  const UInt_t  getParams() ();`SpecTcl uses a `CEvent`
                                object to represent unpacked parameters from
                                an event.   This object is self-resizing.
                                It looks like an array but if an element is
                                referenced out of range of the allowed indices,
                                it is expanded as needed.

The `CEvent` object
                                is instantiated by SpecTcl with an initial size.
                                This method returns the initial number of elements
                                in a `CEvent`.  Note that
                                since these objects are recycled from event
                                to event, tuning the initial size has no
                                amortized effect on performance as all
                                of these objects eventually grow to the appropriate
                                size (usually quite quickly).

`  const UInt_t  getListSize();`Determines the number of `CEvent`
                                objects that are collected for each pass through
                                the histogrammer.

`  const CAnalyzer*  getAnalyzer();`Returns a pointer to the analyzer object.
                                This is deprecated in favor of the
                                `GetAnalyzer` method
                                in the `SpecTcl` API
                                class.

`  const CTCLHistogrammer*  getHistogrammer();`Returns a pointer to the histogrammer object.
                                This is the special event sink pipeline element
                                that performs gating and histogramming

Note that this is deprecated in favor of the
                                `GetHistogrammer` method
                                if the `SpecTcl` API class.

`  const CTKRunControl*  getRunControl();``CRunControl` objects are
                                responsible for starting and stopping playback
                                from data sources as well as providing a
                                callback when data can be read from a source.

The drun control object used by default for
                                `CTclGrammerApp` objects
                                is a `CTKRunControl` object
                                that uses file events to know when data are ready
                                from a data source.  This method returns a pointer
                                to the run control object currently in use.

`  const CXamineEventHandler*  getXamineEvents();`The Xamine displayer communicates with the
                                its client via Unix IPC objects.  Shared memory
                                is used to provide bulk spectrum data and metadata
                                to Xamine.  Message based IPS are used to
                                pass events from Xamine to SpecTcl.

An `XamineEventHandler`
                                object is an object that is used to mediate
                                message traffic from Xamine to SpecTcl.
                                It handles both gate notifictions and notifications
                                of button clicks for user button boxes.

This method returns thye current instance
                                of the `CXamienEventHandler`.
                                This may not be meaningful if a displayer other
                                than Xamine is used.

`  const   CRunControlPackage*  getRunControlPackage();`SpecTcl's commands are grouped into sets of
                                related functionality called
                                *command packages*.  Command
                                package objects,
                                derived from `CTCCommandPackage`,
                                not only contain a set of commands
                                but also provide services that can be accessed by
                                the commands in the package.

This scheme also servers to insulate SpecTcl's
                                command functionality from the language that
                                invokes it... to some extent.

This method returns a pointer to the run control
                                command package.  This package provides services
                                for the run control commands;
                                **start** and
                                **stop**.

`  const CParameterPackage*  getParameterPackage();`See `getRunControlPackage`
                                for background information about command
                                packages.  `CParameterPackage`
                                is a package containing the commands that manipulate
                                SpecTcl parameter definitions.  This includes both
                                the **parameter** and
                                **psuedo** commands.

This method returns a pointer to the parameter
                                package object.

`  const CSpectrumPackage*  getSpectrumPackage();`The `CSpectrumPackage`
                                object contains and provides services for
                                commands that affect spectra.  These include
                                **spectrum**,
                                **clar**,
                                **sbind**,
                                **unbind**,
                                **channel**,
                                **swrite** and
                                **sread**.
                                This method returns a pointer to this package
                                object.

`  const CDataSourcePackage*  getDataSourcePackage();`The `CDataSourcePackage`
                                contains and provides services for commands that
                                provide access to SpecTcl data sources.
                                These include the **attach**
                                and **ringformat** classes.
                                Older versions of SpecTcl also provide
                                access to the obsolete **tape**
                                command.

This method returns a pointer to the
                                data source package object.

`  const CGatePackage*  getGatePackage();``CGatePackage` contains and
                                provides services for commands that have to do
                                with gates.  These commands include:
                                **gate**,
                                **apply** and
                                **ungate**.

This method returns a pointer to the
                                `CGatePackage` object used
                                by SpecTcl.

`  const CTCLVariable  getTclDisplaySize();`Returns a `CTCLVariable` that,
                                in `BindTCLVariables`
                                is bound to the Tcl variable
                                DisplayMegabytes.

This can be set to be the default number of
                                display shared memory megabytes.  This must
                                be done prior to the call to
                                `SourceLimitScripts`.
                                One way to accomplish this is to override
                                `SourceLimitScripts`
                                and replace it with something like:

```
void MySpecTclApp::SourceLimitScripts(CTCLInterpreter& interp)
{
    CTCLVariable displaySize = getTclDisplaySize();
    displaySize.Bind();
    displaySize.Set("16");
    
    TclGrammerApp::SourceLimitScripts(interp);
}
                            
```

The method above, sets the default value for
                                the display size to 16MB
                                before invoking the base class method to
                                actually source the limit scripts.

`  const CTCLVariable  getTclParameterCount();`Returns an object that represents the
                                Tcl variable that sets the
                                default value for the initial size of
                                new `CEvent` objects.
                                As discussed previously, there's not much to be
                                gained from altering this default as eventually
                                these objects equilibrate in size to the size needed
                                to hold all of the parameters.

`  const CTCLVariable getTclEventListSize();`Returns an object that respresents the Tcl
                                variable that holds the default number of events
                                that are processed by the event processing pipeline
                                before passing events to the event sink pipeline.
                                This can be set prior to the base class executing
                                `SourceLimitScripts`.
                                Note that method may invoke a script that overrides
                                the default and that method will also set that
                                parameter.  It is possible that playing with this
                                will have a minor effect on SpecTcl performancde.

`   CMultiTestSource*  getTestDataSource();`Returns the object that provides test data
                                for SpecTcl prior to first being attached
                                to a real data source.  It's possible,
                                once you have that object to add or select other
                                than the default test source (fixed length
                                events with gaussian parameters).

One potential use for this would be to hook
                                directly to some event simulator, although
                                much simpler would be to teach SpecTcl to analyze
                                the saved event files from such a simulator.

`   CDisplayInterface*  getDisplayInterface();`Provides a pointer to the current display
                                interface.  This object provides methods
                                to manage displayers that can be used by
                                SpecTcl.

The second set of methods we will document are mutators.
                    A mutator is a method that allows you to modify internal
                    attributes of an object.  These methods are all intended
                    to be used by derived classes and therefore are all
                    protected.



`   void  setDisplaySize (const UInt_t  am_nDisplaySize);`Sets the display memory size in megabytes.  This
                                must be called after
                                `SourceLimitScripts` to
                                override the value in those scripts or prior to
                                set the default value.   It should also be
                                called prior to
                                `CreateDisplays` which
                                actually sets up the display shared memory.

`   void  setParams (const  UInt_t  am_nParams);`Sets the number of parameters that will be used
                                as the initial size for `CEvent`
                                vectors.   To override the user's settings, this
                                should be called after
                                `SourceLimitScripts`, otherwise
                                it is used as a default value for that
                                parameter if it is not set in the user's scripts.

As previously discussed, setting this has
                                essentially no impact on SpecTcl's performance
                                due to the autosizing and recycling of parameter
                                vectors.

`                                       void 
                                 setListSize (const  UInt_t  am_nListSize);`Sets the event list size.  This is the number
                                of events that is analyzed by the event processing
                                pipeline before those events are passed to the
                                event sink pipeline for histogramming and
                                other processing.

This set of methods are virtual and therefore can be overridden.
                    These methods are all exposed in the
                    `MySpecTclApp` class in the SpecTcl
                    Skeleton.  In that class, the base class method is invoked.
                    You can add code as needed to meet your needs.



`   void RegisterEventProcessor( CEventProcessor&  rEventProcessor, const  char*  name  = 0);`Not actually a virtual method, this method is
                                used to add an event processor to the end of
                                the event processing pipeline.
                                `rEventProcessor`, is the
                                processor to add and `name`,
                                if supplied is a name associated with the event
                                processor.  If `name`
                                is not supplied, one is assigned.

` virtual   void  BindTCLVariables( CTCLInterpreter&  rInterp);`This is called to bind SpecTcl's special Tcl
                                variables to this object's
                                `CTCLVariable`
                                members.  Doing this allows those objects
                                to access the underlying Tcl variables.
                                Variables bound and created include:



- `tcl_rcFilename`
                                          The name of the early Tcl initialization
                                          file.
- `DisplayMegabytes`
                                          Number of megabytes of display shared
                                          memory allocated.
- `ParameterCount`
                                          Number of parameers allocated in the
                                          initial create of `CEvent`
                                          objects.
- `EventListSize`
                                          Number events analyzed by the analysis
                                          pipeline before passing them on to the
                                          sink pipeline.
- `DisplayType`
                                          type of displayer used.

` virtual   void  SourceLimitScripts( CTCLInterpreter&  rInterpreter);`Sources the limit setting scripts
                                (SpecTclInit.tcl) into
                                `rInterpreter`.  All
                                of the following locations are searched and for
                                the reasons given:



- The etc subdirectory
                                          of the SpecTcl installation is searched
                                          to provide system defaults that override
                                          the default values compiled in to
                                          SpecTcl.
- The user's home directory is searched
                                          to provide account wide settings that may
                                          override the system wide settings.
- The current working directory is searched
                                           to provide project specific settings.

` virtual   void  SetLimits();`Updates the SpecTcl Tcl variables from the
                                final tuning values after
                                `SourceLimitScripts`
                                has been executed.

` virtual   void  CreateHistogrammer();`This method creates the event sink pipeline,
                                assigning a pointer to it to
                                `gpEventSinkPipeline`.
                                It then immediately creates a
                                `CHistogrammer` object
                                saving it's pointer in
                                `gpEventSink` and adding it
                                to the end of the event sink pipeline.

In addition an observer is attached to the
                                spectrum dictionary (part of the histogrammer).
                                This observer, a
                                `SpectrumDictionaryFitObserver`
                                destroys fits on spectra that are being removed
                                from the spectrum dictionary.

` virtual   void  CreateDisplays();`SpecTcl supports more than one displayer.
                                Currently it supports Xamine, a displayer built
                                directly on Motif and the Xt/X11 toolkit and
                                Spectra, a displayer build on Root.
                                This method sets up a factory of display
                                interfaces.
                                It stocks it with creators for
                                Xamine, Spectra and headless (batch) mode.

` virtual   void  SelectDisplayer();`Selects and starts the displayer whose name is
                                stored in the Tcl variable
                                `DisplayType`.
                                `DisplayType` must have been
                                set prior to
                                `SourceLimitScripts`.

The displayer process is started if appropriate.

` virtual   void  SetUpDisplay();`Sets up communication between SpecTcl and the
                                displayer.  Specifically, when gates are
                                created or destroyed, when spectra have gates
                                applied to them or are ungated, the displayer
                                may provide visual cues.  This method sets up
                                observers on the SpecTcl side that
                                detect appropriate changes and communicate
                                with the selected displayer so that this
                                information is updated by the displayer..

` virtual   void  SetupTestDataSource();`SpecTcl has a test data source.  If analysis
                                is started, prior to attaching to a data source,
                                the test source will supply data.  The
                                test data source is, by default, a
                                `CMlutiTestSource` which
                                is can be a container for several types of
                                data sources.

This method establishes that data source
                                and selects its default data source.
                                The default data source delivers fixed sized
                                events that contain several parameters of
                                gaussian distributed parameters.

The SpecTcl skeleton files can analyze data
                                from the default test source without modification.
                                This is one way to use and become familiar with
                                SpecTcl.

` virtual   void  CreateAnalyzer( CEventSink*  pSink);`Creates and attaches the analyzer to the system.
                                The analyzer is the object that controls the
                                flow of data from a data source through the
                                analysis pipeline and to the event sink
                                pipeline.

By default a `CTclAnalyzer`
                                is instantiated and hooked in to SpecTcl.
                                A pointer to the analyzer object is stored
                                in `gpAnalyzer` as well
                                as in the attribute
                                `m_pAnalyzer`.  Both should
                                be updated to change the analyzer, if that's
                                desired.

` virtual   void  SelectDecoder( CAnalyzer&  rAnalyzer);`Sets the initial buffer decoder. Note that
                                in most cases, SpecTcl's
                                **attach** command will
                                select a new buffer decoder object to match the
                                `-format` value, implied by
                                or explicit in the command.

` virtual   void  CreateAnalysisPipeline( CAnalyzer&  rAnalyzer = 0);`This is a pure virtual method and therefore
                                must be implemented by any subclass that
                                can be instantiated.  The code in this
                                method should create and add elements
                                to the event processing pipeline.

`RegisterEventProcessor`
                                is provided as a convenience method for
                                adding event processors to the analyzer.
                                Note that event processors are a property
                                of the `CTclAnalyzer`
                                class and its descendents.

` virtual   void  AddCommands( CTCLInterpreter&  rInterp);`Adds SpecTcl specific commands to the
                                Tcl interpreter
                                `rInterp`.
                                The base class method creates and adds
                                all of the command packages that hold most
                                of SpecTcl's commands.

`   void  SetupRunControl();`Not virtual and therefore cannot be overridden,
                                this method creates a new
                                `CTkRunControl`
                                object, stores a pointer to it in 
                                `gpRunControl` which
                                establishes it as the run control object
                                that SpecTcl uses.  The object's pointer is
                                also stored in the attribute
                                `m_pRunControl`.

` virtual   void  SourceFunctionalScripts( CTCLInterpreter&  rInterp);`Sources functional setup scripts into
                                `rInterp`.  The
                                functional setup scripts are those named
                                SpecTclRC.tcl.  SpecTcl
                                will first run any script by this name that
                                exists in the user's home directory.  Next it
                                will run any script by that name that exists in
                                the current working directory.

` virtual   int  operator()();`Entry point.  This method invokes all of the
                                initialization methods in turn.
                                It should return
                                TCL_OK if successful
                                and TCL_ERROR on
                                any failure.

The remainder of the methods we'll document are
                    utility functions.  These are protected and therefore
                    can only be called from methods in this class or a
                    class derived from this class
                    (e.g. `MySpecTclApp`).



` static   void  UpdateUInt( CTCLVariable&  rVar,  UInt_t&  rValue);`This utility method accepts a
                                Tcl variable object
                                (`rVar`) which is
                                supposed to hold an
                                unsigned integer and sets
                                `rValue` to the value
                                of that integer.  If the variable does not
                                exist in the Tcl interpreter, no error
                                is thrown and the `rValue`
                                is un-modified.

` static   void  UpdateString( CTCLVariable&  rVar,  std::string&  rString);`Similiar to
                                `UpdateUInt`
                                but the Tcl variable is an arbitrary
                                string.

` static   std::string  SourceOptionalFile( CTCLInterpreter&  rInterp,  std::string  filename);`This method attempts to source the file
                                `filename` into the
                                interpreter `rInterp`.
                                It is not an error for the file to not exist.
                                That's the meaning of the
                                "optional" part of this method's name.

The return value from this method is an empty
                                string on success (including missing file)
                                and an error message string if an error occured
                                (such as the script failing).

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CEventBuilderEventProcessor | Up | CHistogrammer |
