|  |  |  |
| --- | --- | --- |
| SpecTcl Programming Reference. |
| Prev |  | Next |


---

# <a name="AEN37"></a>SpecTcl

<a name="AEN41"></a>## Name

SpecTcl -- API Singleton class.

<a name="AEN44"></a>## Synopsis

```
SpecTcl
```

<a name="AEN48"></a>## DESCRIPTION

`SpecTcl` is a singleton class that
                    provides an application programming interface to the
                    functions SpecTcl considers public.  While every method in
                    this class is available in some way as a public method
                    in some other SpecTcl class, this set of interfaces is
                    gauranteed to remain avaiable through modifications to
                    SpecTcl's internal structures and algorithms.

As a singleton, the constructor and destructor of this
                    class are declared as private.  Use
                    the `getInstance` method to
                    obtain a pointer to the single instance of this class.

<a name="AEN55"></a>## METHODS



` static   SpecTcl*  getInstance();`Returns a pointer to the singleton instance
                                of this class.   This is the only supported
                                way to get an instance of this class.
                                Any two calls to `getInstance`
                                will return the same value.

There is no gaurantee that an instance of this
                                class will exist until the first call to this
                                method.

`   void  addBufferDecoder( std::string  type,  CAttachCommand::CDecoderCreator*  creator);`Adds a new buffer decoder to SpecTcl.
                                `type` is a format type
                                value that can be given to
                                **attach** `-format`.
                                `creator` is an instance
                                of a class that knows how to create a
                                buffer decoder that can unravel the data in
                                event files of the form specified by
                                `type`

The programming guide contains a chapter
                                that describes buffer decoders, what they are
                                for, how to write one and add it to the
                                SpecTcl **attach** command.

`   UInt_t  AssignParameterId();`Each SpecTcl parameter must have a unique id.
                                This id is an integer index into the
                                flat parameter array that SpecTcl uses
                                to drive its gate checking and histogramming.
                                This method allocates a new, unique parameter
                                id.

This method should never return the same
                                integer twice. You can not gaurantee that
                                values from this method will be sequential
                                although they mostly will be.  Specifically,
                                `AssignParameterId`
                                will not assign a parameter Id that's already
                                been assigned.

Imagine, for example, that this method just
                                returned 1234.  Suppose
                                further a SpecTcl command or script line looked like:
                                **parameter somename 1235**.
                                The next call to `AssignParameterId`
                                will not return 1235 but an
                                integer that has not already been associated with
                                a parameter.

`   CParameter*  AddParameter( std::string  name,  UInt_t  Id,  std::string  Units);`Adds a new parameter definition to SpecTcl.
                                This method is the simplest way to add a parameter.
                                `name` is the name to be
                                givent to the new parameter.  It is an
                                error to assign the same name to two parameters.

`Id` is the new parameter's
                                id.  This usually should be a value  gotten
                                from a call to `AssignParameterId`.

`Units` are the units of
                                measure to assign to assign to the parameter.
                                This can be an empty string if the parameter
                                does not have an appropriate unit of measure
                                (e.g. a raw ADC value).

The method's return value is a pointer to the
                                new `CParameter`
                                object created and entered in the SpecTcl
                                parameter dictionary.

`   CParameter*  AddParameter( std::string  name,  UInt_t  id,  UInt_t  scale);`Adds a new parameter definition.  All of the
                                parameters are the same as the previous overload
                                for this method except that `scale`
                                is the number of bits used by the parameter.  This
                                is suitable for use with e.g. raw ADC values.

As with all `AddParameter`
                                overloads, the return value is a pointer
                                to the new `CParameter`
                                object that was created and entered in the
                                parameter dictionary.

`   CParameter*  AddParameter( std::string  name,  UInt_t  id,  UInt_t  scale,  Float_t  low,  Float_t  high,  std::string  units);`Another overload that adds a new parameter
                                to SpecTcl.  `low` and
                                `high` define range
                                limits for the parameter.    These
                                define a mapping from raw parameter space to some
                                world coordinate space.  The value 0
                                maps to `low` and the
                                value 2**scale - 1 maps
                                to `high`.

In general, it is better to use tree parameters
                                and compute the actual value of the parameter
                                than to use this confusing mapped parameter
                                scheme.  This scheme came into being for
                                SpecTcl-2.0 and is only retained for
                                compatibility with existing SpecTcl code.
                                It is normally used in conjunction with
                                *Mapped spectra*.

As with all overloads of
                                `AddParameter`, the
                                return value is a pointer to the
                                `CParameter` object
                                this call created.

`   CParameter*  RemoveParameter( std::string  name);`If a parameter named `name`
                                has been defined it is removed from SpecTcl's
                                parameter dictionary and a pointer to a dynamically
                                allocated copy of that `CParameter`
                                object is returned.   The caller must
                                delete that object to
                                prevent memory leaks.

If there is no parameter named `name`
                                in the parameter dictionary, a null pointer is
                                returned from this method.

`   CParameter*  FindParameter( std::string  name);`Locates and returns a pointer to the parameter
                                object named `name`.  If there
                                is no matching parameter, a null pointer is returned.
                                Note that this is a pointer to the actual parameter
                                in the SpecTcl parameter dictionary and any
                                changes to it are reflected in the analysis
                                SpecTcl performs.

`   CParameter*  FindParameter( UInt_t  Id);`Returns a pointer to a parameter given its
                                `Id`.  If no parameter
                                has that id, the method returns a null pointer.

`   ParameterDictionaryIterator  BeginParameters();`, `   ParameterDictionaryIterator  EndParameters();`These two methods support iteration of the
                                SpecTcl parameter dictionary.
                                `BeginParameters`
                                returns an iterator that acts like a pointer
                                to the first element of the parameter
                                dictionary. ParameterDictionaryIterator
                                objects support being incremented.  When incremented,
                                the "point" to the next dictionary element.
                                When the last element in the dict has been
                                pointed to, incrementing an iterator
                                gives it the value returned by
                                `EndParameters`.

The ParameterDictionaryIterator
                                is an STL std::pair<std::string, CParameter>
                                where the first element of the pair is the name of the
                                parameter and the second is a copy of the
                                `CParameter` with that
                                name.

Iteration is only good for read-only access to the
                                parameters as iterators 'point' to copies rather
                                than references or pointers to the actual
                                items in the dictionary.

`   UInt_t  ParameterCount();`

`   CSpectrum*  CreateSpectrum( std::string  Name,  SpectrumType_t  type,  DataType_t  dataType,  std::vector<std::string>  parameters,  std::vector<UInt_t>  channels,  std::vector<Float_t>*  pLows,  std::vector<Float_t>*  pHighs);`Creats a new histogram and returns a pointer to it.
                                The new spectrum has been dynamically created and
                                must, eventually, be destroyed with
                                delete.

For SpecTcl's histogramming core and
                                command set to know about the new spectrum
                                it must be passed to
                                `AddSpectrum` (see below).
                                If this is not done, the caller has created
                                a spectrum that can be used by them but is
                                invisible to SpecTcl.

`Name` specifies a new name
                                to give to the spectrum.  If the spectrum will
                                be entered in the spectrum dictionary, this name
                                must not have been given to any other spectrum
                                in the spectrum dictionary.

`type` is the type  of
                                the spectrum.  This can be any value that
                                the enumerated type SpectrumType_t
                                can take and determines the type of the spectrum.
                                Note that we recommend that rather than using
                                this method to create a spectrum you use one of
                                the more specific creators documented below.

`type`, is the data type
                                for each channel of the spectrum.  This
                                can be one of keLong (recommended),
                                keWord or keByte,
                                and determines how many counts a spectrum channel
                                can have before the channel rolls over.

`parameters` is a vector
                                of the names of parameters that will be used
                                by the spectrum.  Note that some spectrum
                                types may need to specify x and y parameter lists,
                                see below.

`parameters` specifies the
                                parameters used by the spectrum.  The use of only
                                a single parameter list means this can only be used
                                to create spectra that don't need to differentiate
                                between X and Y parameters, such as 1D, gamma-1,
                                gamma-2, summary spectra etc.

`channels` is a vector
                                of one or two channel counts for the x and optional
                                y axis.

`pLows` and
                                `pHighs` are pointers to
                                vectors of the low and high limits for each
                                axis respectively.  There must be the same
                                number of `pHighs`
                                as `pLows`.

`   CSpectrum*  CreateSpectrum( std::string  Name,  SpectrumType_t  type,  DataType_t      dataType,  std::vector<std::string>  xParameters,  std::vector<std::string>  yParameters,  std::vector<UInt_t>  channels,  std::vector<Float_t>*   pLows,  std::vector<Float_t>*  pHighs);`Anothr method to create a generic spectrum.  The
                                difference between this and the previous overload
                                is that `xParameters` and
                                `yParameters` allow specification
                                of a set of parameters for the X and Y axes as are
                                needed for e.g. 2-d Spectra, 2-d Sum spectra or
                                Gamma Deluxe (particle-gamma) spectra.

Similarly, `pLows` and
                                `pHighs` provides a
                                set of limits for all axes.  The `channels`
                                vector can have channel counts for both axes.  These
                                are vectors to allow for future expansion in the
                                SpecTcl spectrum types

`   CSpectrum*  CreateSpectrum( std::string            Name,  SpectrumType_t         type,  DataType_t    dataType,  std::vector<std::vector<std::string> >  parameters,  std::vector<UInt_t>  channels,  std::vector<Float_t>*  lows,  std::vector<Float_t>*  highs);`Provides a spectrum creator for when parameters
                                must come as a vector of vectors.  For example
                                for a gamma summary spectrumw where each X
                                channel of the spectrum may require more than
                                one parameter.

The next several methods create specific types of spectra.
                    They are the recommended way to create spectra.  Usually
                    the generic methods above are a bit harder to use.



`   CSpectrum*  CreateGammaSummary( std::string Name,  DataType_t dataType,  std::vector<std::vector<std::string> >  parameters,  UInt_t   nChannels,  std::vector<Float_t>*  low,  std::vector<Float_t>*   high);`Creates a gamma summary spectrum.  A gamma summary
                            spectrum, is a two dimensional spectrum whose
                            vertical channel strips are each a gamma spectrum.
                            `parameters` are a vector of
                            parameters for each X channel (vertical strip).
                            The outer vector index is a channel number and
                            the inner vector the set of parameters on that
                            strip.

The `nChannels` parameter is
                            the number of parameters in the Y direction
                            as the number of X channels is determined by the
                            size of the outer vector of
                            `parameters`.  The
                            `low` and
                            `high` vectors are the low and
                            high limits of each vertical strip in the parameter
                            space of the parameters that are histogrammed
                            on it.

`   CSpectrum*  CreateG2DDeluxe( std::string  Name,  DataType_t  dataType,  std::vector<std::string>  xParameters,  std::vector<std::string>  yParameters,  std::vector<UInt_t> channels,,  std::vector<Float_t>*  pLows,  std::vector<Float_t>*  pHighs);`Creates a gamma deluxe spectrum.  This is a spectrum
                            multiply incremented spectrum with separate x and
                            y parameters sets.  The spectrum is incremented
                            for each pair of parameters present in the spectrum.
                            `channels` is a two element
                            vector containing, in order, the number
                            of channels on the X and Y axis.

`pLows` and
                            `pHighs` are both two
                            element vectors that specify, in order, the low
                            and high parameter space limits of the X and Y axis.

`   CSpectrum*  Create1D( std::string  name,  DataType_t  dataType,  CParameter&  parameter,  UInt_t  channels);`Creates a 1-d spectrum.  `parameter`
                            is the parmeter histogrammed and the
                            X axis will have `channels`
                            channels.  In this overload, the range of
                            the parameter histogrammed will be
                            [0, `channels)`.

`   CSpectrum*  Create1D( std::string  name,  DataType_t  dataType,  CParameter&  parameter,  UInt_t  channels,  Float_t  lowLimit,  Float_t  hiLimit);`Creates a 1-D spectrum where `lowLimit`
`hiLimit` and `channels`
                            define a transformation between parameter and spectrum
                            channel space.
                            This transformation is:
                            channel = ((parameter- lowLimit)*channels(hiLimit-lowLimit)).
                            This provides a uniform mapping of the interval
                            [lowLimit, hiLimit) to 
                            [0, channels).

`   CSpectrum*  Create2D( std::string  name,  DataType_t  dataType,  CParameter&  xParameter,  CParameter&  yParmaeter,  UInt_t  xChannels,  UInt_t  yChannels);`Creates a 2-d spectrum with 1:1 parameter:channel
                            space mapping.  `xParameter`
                            is on the X axis and `yParameter`
                            on the Y.  There are `xChannels`
                            on the X axis that map to the `xParameter`
                            value range [0, xChannels).
                            There are `yChannels` on the
                            Y axis that map the `yParameter`
                            value range [0, yChannels).

`   CSpectrum*  Create2D( std::string  name,  DataType_t  dataType,  CParameter&  xParameter,  CParameter&  yParameter,  UInt_t  xChannels,  Float_t  xLow,  Float_t  xHigh,  UInt_t  yChannels,  Float_t  yLow,  Float_t  yHigh);`Creates a 2-d spectrum with parameter to channel
                            mappings that are not identities.
                            `xChannels`,
                            `xLow` and
                            `xHigh` determine the
                            mapping of the X parameter to channels on the
                            X axis.
                            `yChannels`,
                            `yLow` and
                            `yHigh` determine the
                            mapping of the Y parameter to channels on the
                            Y axis.

The mapping is linear for both parameters.

`   CSpectrum*  CreateG1D( std::string  name,  DataType_t  dataType,  std::vector<CParameter>  parameters,  UInt_t  channels);`Creates a gamma-1d spectrum.  The spectrum
                            increments for all `parameters`
                            present in the event.  This method creates a
                            spectrum with a unit mapping between parameter
                            and X axis channel space.  Thus values from
                            [0, `channels`)
                            are histogrammed.

`   CSpectrum*  CreateG1D( std::string  name,  DataType_t  dataType,  std::vector<CParameter>  parameters,  UInt_t  channels,  Float_t  lowLimit,  Float_t  hiLimit);`Creates a gamma-1D spectrum with potentially non
                            unit mappings between the parameter coorinates
                            and spectrum channels.
                            `lowLimit`, `hiLimit`
                            and `channels` define a uniform
                            mapping between parameter coordinates in the
                            range [lowLimit, hiLimit)
                            and the channel coordinates
                            [0, channels).

`   CSpectrum*  CreateG2D( std::string  name,  DataType_t  dataType,  std::vector<CParameter>  parameters,  UInt_t  xChannels,  UInt_t  yChannels);`Creates a 2-d gamma spectrum with unit mapping
                            between the parameters for both the X and Y
                            axis.
                            `xChannels` is the n umber
                            of axes on the X axis and
                            `yChannels` the number of
                            channels
                            on the Y axis.

`   CSpectrum*  CreateG2D( std::string  name,  DataType_t  dataType,  std::vector<CParameter>  parameters,  UInt_t  xChannels,  Float_t  xLow,  Float_t  xHigh,  UInt_t  yChannels,  Float_t  yLow,   Float_t  yHigh);`Creates a gamma 2d spectrum with potentially non
                            unit mappings between parameter and spectrum
                            axis space.  The mapping on the X axis is
                            determined by
                            `xChannels`,
                            `xLow` and
                            `xHigh` such that the
                            parameter space
                            [xLow, xHigh) is mapped linearly
                            to [0, xChannels).
                            The mapping on the Y axis is similarly determined by
                            `yChannels`,
                            `yLow` and
                            `yHigh`.

`   CSpectrum*  CreateBit( std::string  name,  DataType_t  dataType,  CParameter&  parameter,  UInt_t  channels);`Creates a bit map spectrum.  Bit map spectra are
                            incremented once for every bit set in the
                            `parameter`.   There
                            are `channels` channels in the
                            spectrum, one for each bit that you want monitored.

`   CSpectrum*  CreateBit( std::string  name,  DataType_t  dataType,  CParameter&  parameter,  UInt_t  channels,  UInt_t  lowBit);`Creates a bit map spectrum that covers
                            `channels` bits of the
                            parameters beginning with the low bit
                            designated by `lowBit`.

`   CSpectrum*  CreateSummary( std::string  name,  DataType_t  dataType,  std::vector<CParameter>  parameters,  UInt_t  channels);`Creates a summary spectrum. A summary spectrum is
                            a 2-d spectrum whose vertical strips (defined by
                            a single x channel) are 1-d spectra.  Summary
                            spectra make monitoring a set of similar detectors
                            easy.  `parameters` are
                            the set of parameters to histogram and define the
                            number of x channels (one for each parameter).
                            `channels` defines the
                            number of y channels.  This method defines
                            a unit mapping between parameter values and
                            Y channels.

`   CSpectrum*  CreateSummary( std::string  name,  DataType_t  dataType,  std::vector<CParameter>  parameters,  UInt_t  nChannels,  Float_t  low,  Float_t  high);`Creates a summary spectrum on the `parameters`.
                            This spectrum will have a mapping from parameter to
                            spectrum y channel coordinates that is a linear map
                            from parameter coordinates in the range
                            [`low`, `high`)
                            to channel coordinates
                            [0, `nChannels`).

`   CSpectrum*  CreateGamma2DD( std::string  name,  DataType_t  dataType,  std::vector<CParameter>  xParameters,  std::vector<CParameter>  yParameters,  UInt_t  xChannels,  Float_t  xLow,  Float_t  xHigh,  UInt_t  yChannels,  Float_t  yLow,  Float_t  yHigh);`Creates a gamma 2d deluxe spectrum.  This type of
                            spectrum increments for all combinations of pairs of
                            `xParameters` and
                            `yParameters` that are
                            defined in the event.
                            The mapping between parameter and channel coordinates
                            is lineary but not necessarily unity.

`xChannels`,
                            `xLow`, and
                            `xHigh` define a linear
                            mapping between parameter
                            X parameter values in the range
                            [`xLow`, `xHigh)`
                            and [0, `xChannels`)
                            on the X axis.
                            On the Y axis a similar mapping is defined by:
                            `yChannels`,
                            `yLow`, and
                            `yHigh`

`   CSpectrum*  Create2DSum( std::string  name,  DataType_t   dataType,  std::vector<CParameter>  xParameters,  std::vector<CParameter>  yParameters,  UInt_t  xChans,  Float_t  xLow,  Float_t  xHigh,  UInt_t  yChans,  Float_t  yLow,  Float_t  yHigh);`Creates a 2-d sum spectrum.  This spectrum is
                            essentially the spectrum that would result from
                            summing 2-d spectra on
                            `xParameters[0]`,
                            `yParameters[0]`, ...
                            The mapping from parameter to channel space
                            in both X and Y is
                            defined in the usual way using the low, high and
                            channel count parameters.

`   CSpectrum*  CreateStripChart( std::string  name,  DataType_t   dataType,  CParameter counts,  CParameter time,  UInt_t  channels,  Float_t  xLow,  Float_t  xHigh);`Creates a strip chart spectrum.  Strip chart spectra
                            plot the `time` parameter value
                            against the accumulated `counts`
                            parameter.  `xLow` and
                            `xHigh` are an initial range
                            the X axis covers in the `time`
                            parameter.

If the `time`
                            parameter value is outside the range of the
                            current X axis limits, the X axis will be shifted
                            to cover that new value.    The range covered will
                            be the same as before, however.
                            This shift provides the strip chart functionality
                            that gives this spectrum its name.  Note that
                            currently, there's no command or user interface
                            method to shift the spectrum back to its original
                            range, however the axis can shift backwards
                            if the time value is before the
                            current left limit of the spectrum, which effectively
                            provides this functionality automatically.

Note that data shifted off the edge of the spectrum
                            is  lost. Note as well that data are cumulative, thus
                            if the binning is such that two time values fall
                            in the same channel, the resulting channel value
                            will be the sum of the two `counts`
                            parameters for those two events (summed with any prior
                            value that channel might have).

`   void  AddSpectrum( CSpectrum&  spectrum);`Adds a spectrum to SpecTcl's spectrum dictionary.
                            There cannot be a spectrum with this name
                            in the dictionary else an exception will be thrown.

`   CSpectrum*  RemoveSpectrum( std::string  name);`Remove the spectrum named `name`
                            from the SpecTcl spectrum dictionary.  The spectrum
                            no longer exists from SpecTcl's point of view.
                            If the spectrum was produced by one of the methods
                            above, you need to delete to free
                            it to avoid memory leaks.

`   CSpectrum*  FindSpectrum( std::string  name);`, `   CSpectrum*  FindSpectrum( UInt_t  id);`Attemts to locate the spectrum named `name`,
                            or has the id `id`,
                            in SpecTcl's spectrum dictionary.   A pointer to the
                            spectrum object is returned if found or a null
                            pointer is returned if there no spectrum
                            matching the name.

`   SpectrumDictionaryIterator  SpectrumBegin();`, `   SpectrumDictionaryIterator  SpectrumEnd();`These methods support iteration through the
                            SpecTcl spectrum dictionary.
                            `SpectrumDictionaryIterator`
                            objects are pointer like objecs.  They
                            'point' to a
                            `std::pair<td::string, CSpectrum*>`.

The first item of each pair is the name of the spectrum.
                            The second itesm is a pointer to the
                            spectrum with that name.

`SpectrumDictionaryIterator`
                            objects can be incremented (`operator++`).
                            Incrementing an iterator 'points' it to the next
                            object in the container.

`SpectrumBegin` points  to the first
                            object in the dictionary.  Iterating through the dictionary
                            has finishe when incrementing produces the value
                            returned by
                            `SpectrumEnd`.

`   UInt_t  SpectrumCount();`Returns the numbr of entries in the SpecTcl
                            spectrum dictionary.

`   void  addSpectrumDictionaryObserver( SpectrumDictionaryObserver*  observer);`Adds a new observer to the spectrum dictionary.
                            See e.g. [https://en.wikipedia.org/wiki/Observer_pattern](https://en.wikipedia.org/wiki/Observer_pattern)
                            for information about the observer pattern and observers.

Spectrum dictionary observers derived from the
                            `CDictionaryObserver` templated
                            class (defined in Dictionary.h).
                            They have a `onAdd`, called
                            when a new entry is added to the dictionary, and
                            a method called `onRemove`
                            called when an entry is removed from the
                            dictionary.

Both obserer entries are passed two parameters.
                            The first is an `std::string`
                            that holds the name of the spectrum being
                            added or removed/  The secod i a a
                            `CSpectrum` reference which is
                            a reference to the spectrum being added or removed.

`   void  removeSpectrumDictionaryObserver( SpectrumDictionaryObserver*  observer);`Removes a spectrum dictinoary observer from the list
                            of observer methods.  The `observer`
                            object is no longer called.

`   void  ClearSpectrum( std::string  name);`Clears the spectrum named `name`.
                            If there is no spectrum named `name`,
                            an exception (`CDictionaryException`).

`   void ClearAllSpectra();`Iterates through the spectrum dictionary
                            zeroing the spectra.

The next set of methods manipulate gates and the gate dictionary.
                Note that as with Spectra, the act of creating a gate is
                separate from the act of making it known to SpecTcl's
                commands and histogramming core by entering it into a gate
                dictionary.



`   CGate*  CreateGate( CGateFactory::GateType  gateType,  std::vector<std::string>  names);`Creates a new compound gate whose dependent
                            gates are `names`.   Legal gate
                            types for this method are
                            And, bandcontour,
                            Not, Or,
                            trueg, falseg
                            or deleted.

Note that for
                            trueg, falseg
                            or deleted,
                            the `names` vector must be empty.

Note that the gate has no name.  It is given its name
                            when `AddGate`.

The method returns a pointer to the new,
                            dynamically create gate object.

`   CGate*  CreateGate( CGateFactory::GateType  gateType,  std::vector<std::string>  parameters,  std::vector<FPoint>  points);`, `   CGate*  CreateGate( CGateFactory::GateType gateType,  std::vector<FPoint>  points,   std::vector<UInt_t>  parameters);`Creates a primitive gate.  `parameters`
                            are the names of the parameters the gate is defined on.
                            `points` are x/y points that define
                            the gate.  `gateType` can be any
                            gate that requires a set of points.

The second form of this method provides the
                            `parameters` vector as a vector
                            of parameter ids rather than names.

`   CGate*  CreateGate( CGateFactory::GateType  gateType,  std::vector<std::string>  rparameters,  long  comparison);`Creates a bit mask gate of the type
                            specified by `gateType`.
                            `rparameters` specifies the
                            parameters required for the gate.
                            `comparison` is the type
                            of comparison to perform.

`   CGate*  CreateTrueGate();`Creates a true gate. A true gate is true for
                            every event regardless of the set of parameters
                            defined by that event or their values.

`   CGate*  CreateFalseGate();`Creates a false gate.  False gates are false
                            for all events regardless of the parameters
                            defined by an event and its values.

`   CGate* CreateBand ( std::string  xparameter,  std::string  yparameter,  std::vector<FPoint>  points);`Defines a band gate.  A band gate is defined on
                            a pair of parameters.  `xparameter`
                            defines the x coordinate of a point in two dimensional
                            space while `yparameter` defines
                            the y coordinate.  Both parameters must be present and
                            the point defined by them must be below the polyline
                            defined by the array of `points`.

`   CGate*  CreateContour( std::string  xparameter,  std::string  yparameter,  std::vector<FPoint>  points);`Defines a contour gate.  The parameters have the
                            same meaning as for `CreateBand`,
                            however the gate is true for events only if both
                            `xparameter` and
                            `yparameter` are present and
                            the resulting point falls inside the closed shape
                            defined by `pointts`

For pathalogical closed shapes, note that
                            inside-ness is defined by the
                            *odd crossing rule*.
                            This means that if you draw a  ray from the point
                            defined by the event in any direction, the point is
                            inside if an odd number of edges of the shape are
                            crossed and outside if an even number are crossed.
                            This provides a consistent definition of inside-ness
                            reagardless of how pathalogically shaped the
                            contour is.

`   CGate*  CreateBandContour( std::string  firstBand,  std::string  secondBand);`Creates a contour by joining together the endpoints
                            of the two band `firstBand`
                            and `secondBand`.  An exception
                            is thrown if these two gates are not bands.
                            The resulting gate is really a contour and not
                            a compound gate.

This gate is useful for detectors that produce a
                            particle id spectrum that looks like a set of
                            hyperbolae.  One can draw bands between each of the
                            particle groups an then form particle ID groups
                            by creating contours from adjacent gates.

The intent is that if `firstBand`
                            is upper and `secondBand` lower,
                            the resulting gate is essentially
                            firstBand and not secondBand, however
                            the joining of the end points together may slightly
                            violate that expression near the gate edges.

`   CGate*  CreateNotGate( std::string  name);`Creates a not gate using `name`
                            as the dependent gate.  The resulting gate is true
                            only for events for which the gate `name`
                            is false.  For all other events it is false.

`   CGate*  CreateAndGate( gateNames gateNames);`Creates an And gate using `gateNames`
                            as the gate's dependent gates.  This gate is only true
                            if *all* of the gates in
                            `gateNames` are true.

`   CGate*  CreateOrGate( std::vector<std::string>  gateNames);`Creates an or gate whose dependent gates are
                            `gateNames`.  This gate
                            is only true for events in which
                            *at least* of the
                            gates in `gateNames` is also
                            true.

`     CGate*  CreateCut( std::string  parameter,  Float_t  low,  Float_t  high);`Creates a gate that is a cut on 
                            `parameter`.   The cut is
                            defined by the x coorinates of
                            `low` and
                            `high`.  The gate is true
                            only if it defines `parameter`
                            and the value is between `low`
                            and `high`

`   CGate*  CreateGammaCut( Float_t  low,  Float_t  high,  std::vector<std::string>  parameters);`Creates a gamma cut.  The cut is defined by
                            `low` and
                            `high`.   The parameters
                            involved in the gate are
                            `parameters`.

The gamma cut is intended to be applied to a gamma
                            spectrum as a fold.  Folds are a mechanism to untangle
                            sequential decay cascades.  If this gate is applied
                            as a fold to a gamma spectrum, the spectrum is incremented
                            if at least one parameter satisfies the gate and
                            is incremented for all parameters that are not
                            in the gate.  The resulting histogram's peaks
                            are those gamma rays that are emitted in coincidence
                            with the gamma ray energy in the peak the gate is
                            set on.

`   CGate*  CreateGammaBand( std::vector<FPoint>  points,  std::vector<std::string>  parameters);`Creates a gamma band.  This is also intended to be
                            used as a fold in which case the spectrum
                            is incremented only for pairs of parameters
                            that do not satisfy the gate.   Gamma bands
                            are probably not as useful as gamma contours since
                            2-d Gamma spectra tend to make lumps out of
                            pairs of gamma rays that are emitted in coincidence.

`   CGate*  CreateGammaContour( std::vector<FPoint>  points,  std::vector<std::string>  parameters);`Creates a gamma contour from the
                            `points` defined on the
                            `parameters` parameters.
                            This is intended to be used as a fold.

`   CGate*  CreateMaskEqualGate( std::vector<std::string>  rParameterName,  long  Compare);`Creates a mask-equality gate.  The gate will
                            be true for events that define
                            `rParameterName` and for which
                            the value of that parameter will be equal to
                            `Compare`

`   CGate*  CreateMaskAndGate( std::vector<std::string>  rParameterName,  long  Compare);`Creates a mask and gate.  The gate will be true
                            for events that define `rParameterName`
                            and for which the value of that parameter, when bitwise anded
                            with `Compare` is the same as
                            `Compare`.  That is, the parameter
                            has (among others) all bits set that `Compare`
                            has set.

`   CGate*  CreateMaskNotGate( std::vector<std::string>  rParameterName,  long  Compare);`Creates a Mask not gate.  This gate is defined
                            for all events that define
                            `rParameterName` but for
                            which the value of that parameter has all bits
                            set which are not set in `Compare`.

The next set of methods manipulate the gate dictionary.
                Note that the gate creation methods above create the gate but
                don't enter it into the gate dictionary.  To  make the gate
                known to SpecTcl, you must do this by invoking
                `AddGate` below.



`   void  AddGate( std::string  name,  CGate*  gate);`Associates the gate name `name`
                            with the gate `gate` and tries
                            to add it to the gate dictionary.  If a gate
                            by this name already exists; the method throws
                            a `CDictionaryException`
                            exception.

Note that once a gate is known to exist, its
                            definition can be modified by
                            `ReplaceGate` below.

`   void DeleteGate ( std::string  gateName);`Deletes the gate named `gateName`
                            from the gate dictionary.    Note that in order
                            for objects that depend on the gate to behave
                            in a well determined manner, the gate is not
                            actually deleted, but replaced with a
                            false gate.

`   void  ReplaceGate( std::string  gateName,  CGate&  newGate);`Replaces the gate `gateName` with
                            a new gate definition `newGate`.
                            The use of `CGateContainer` objects
                            allows this replacement to happen transparently with
                            respect to dependent gates, spectra to which the
                            gate is applied and spectra folded on the gate.

If `gateName` does not
                            exist a `CDictionaryException`
                            is thrown.

`   CGateContainer*  FindGate( std::string  gateName);`Finds the gate `gateName`
                            in the gate dictionary.  If found, a pointer
                            to its gate container is returned.   If not found,
                            a null pointer is returned.

A `CGateContainer` is a pointer
                            like object that acts like a pointer to an underlying
                            gate.  Gate containers are an additional level of
                            indirection that allow spectra and other gates that
                            depend on a gate to be blissfully unaware of when
                            their gate definitions change.

You can think of the gate container as encapsulating
                            the real gate.  What methods like
                            `DeleteGate` and
                            `ReplaceGate` do is replace
                            the gate that is encapsulated by the gate container.

`   CGateDictionaryIterator  GateBegin();`, `   GateDictionaryIterator GateEnd();`Supports iteration in the gate dictionary. The
                            `CGateDictionaryIterator`
                            is a pointer like object that points to an
                            `std::pair<std::string, CGateContainer>`
                            object.

The first element of the pair is the name of the gate
                            while the second element is the gate container for
                            the gate.  Iteration is accomplished by getting
                            an iterator to the first dictionary element
                            via a call to `GateBegin`.
                            Successive elements of the dictionary are visited
                            by incrementing the iterator.  When the last
                            element is visited, incrementing the iterator
                            returns the value returned by
                            `GateEnd`.

`   UInt_t  GateCount();`Returns a count of the number of elements in the
                            gate dictionary.

`   void  addGateDictionaryObserver( CGateObserver*  observer);`, `   void removeGateDictionaryObserver ( CGateObserver*  observer);`These two methods provide an observer interface
                            to the Gate dictionary.
                            See e.g. [https://en.wikipedia.org/wiki/Observer_pattern](https://en.wikipedia.org/wiki/Observer_pattern)
                            for information about the observer pattern and observers.

`addGateDictionaryObserver`
                            adds the specfied `observer`
                            to the list of gate observers called by the
                            gate dictionary while
                            `removeGateDictionaryObserver`
                            removes `observer` from that list.

A `CGateObserver` object has
                            the following methods:



` virtual   void  onAdd( std::string  name,  CGateContainer&  item);`Called when an entry is added to the dictionary.
                                        `name` is the name
                                        of the new gate and
                                        `item`
                                        is the gate container for the new item
                                        being added.

` virtual   void  onRemove( std::string  name,  CGateContainer&  item);`Called if an entry is removed from the
                                        dictionary.  In normal use this is never
                                        invoked as gates are never deleted,
                                        only modified.

` virtual   void  onChange( std::string  name,  CGateContainer&  gateContainer);`Called when a gate has been changed.
                                        `gateContainer`
                                        is the new gate container.

`   void  ApplyGate( std::string  gateName,  std::string  spectrumName);`

The next set of methods are responsible for managing the event
                processor pipeline.  The event processing pipeline is a sequence
                of objects that are responsible for taking a raw event
                and transforming it into a set of parameteres that can be
                analyzed by the event sink pipeline.  Each stage of the pipeline
                has access to the raw event as well as the set of parameters
                previous stages have unpacked.



`   void AddEventProcessor ( CEventProcessor&  eventProcessor, const  char*  name =  0);`Adds an event processor
                            `eventProcessor`to the end of the
                            event processing pipeline.  If `name`
                            is not a null pointer, it is used as the name of
                            the event processor.  If it is null (not recommended but
                            supported for backwards compatibility), a unique
                            event processor name will be assigned.

`   CTclAnalyzer::EventProcessorIterator  FindEventProcessor( std::string  name);`Given the `name` of an event
                            processor, returns an iterator to it.  If the
                            `name` is not found,
                            the value that is normally returned
                            from `ProcessingPipelineEnd`
                            is returned (see below).

A `CTclAnalyzer::EventprocessorIterator`
                            is a pointer like object.  We'll say more about it
                            when we look at support for iteration.  At this
                            point in time it suffices to know that it can be
                            treated as if it were a pointer to
                            a `std::pair<std::atring, CEventProcessor*>`
                            where the first element of the pair is the name of the event
                            processor pointed to by the second element

`   CTclAnalyzer::EventProcessorIterator  FindEventProcessor( CEventProcessor&  processor);`Finds an event processor in the event processing
                            pipeline given a reference to the event
                            processor object itself.

`   void  InsertEventProcessor(( CEventProcessor&  processor,  CTclAnalyzer::EventProcessorIterator  where, const  char*   name  = 0);`Inserts an event processor
                            (`processor`) in the event
                            processing pipeline at the position prior to that
                            indicated by `where`.  The
                            event processor will be called `name`
                            unless that parameter is a null pointer in which
                            case a unique name will be assigned to it.

Note that `where` is
                            a `CTclAnalyzer::EventProcessorIterator`,
                            an iterator in the STL sense of the term.  For more
                            information about it, see
                            `ProcessingPipelineBegin`
                            and `ProcessingPipelineEnd`
                            below.

`   void  RemoveEventProcessor( std::string  name);`Removes the event processor named `name`.
                            IF there's no event processor named
                            `name`, this is a silent
                            no-op.

`   void  RemoveEventProcessor( CTclAnalyzer::EventProcessorIterator  here);`Removes the event processor 'pointed to'
                            by `here`.  The iterator
                            could have been returned from a call to
                            `FindEventProcessor` or
                            have been the result of iteration (see below).

This operation invalidates the iterator.
                            The results of dereferencing
                            it in the future are undefined.

`   UInt_t  ProcessingPipelineSize();`Returns the number of elements in the event
                            processing pipeline.

`   CTclAnalyzer::EventProcessorIterator  ProcessingPipelineBegin();`, `   CTclAnalyzer::EventProcessorIterator  ProcessingPipelineEnd();`Supports the iteration protocol.
                            `ProcessingPipelineBegin`
                            returns an iterator that 'points' to the
                            first element of the event processing pipeline.
                            The
                            `FindEventProcessor`
                            documentation describes exactly what this
                            'points' to.

Iterators can be incremented in which case they
                            point to the next element of the pipeline (in
                            processing order).  Once the last element of the
                            pipeline has been reached by the iterator,
                            an additional increment returns a value
                            identical to the value that is returned by
                            `ProcessingPipelineEnd`.

The next set of methods manipulate the event sink pipeline.
                The event sink pipeline gains control after the the event
                processing pipeline has processed one or more events.
                it the event sink pipeline initially comes stocked with the
                histogrammer (`CHistogrammer`).
                Filters are also added at the end of the event processing
                pipeline.

This  portion of the API supports additional event
                sink pipeline element types.



`   void  AddEventSink( CEventSink&  sink, const  char*  name  = 0);`Adds a new event `sink` to the
                        end of the event sink pipeline.  If
                        `name` is not a null pointer,
                        it will be the name of the processing element.
                        If it is a null pointer, a unique name
                        will be supplied by SpecTcl.

The histogrammer registers itself as
                        ::Histogrammer.  Event filters
                        register themselves with their filter name.

`   CEventSinkPipeline::EventSinkIterator  FindEventSink( std::string  sinkName);`Returns an iterator to the event sink
                        `sinkName`.  If no such event sink
                        pipeline element exists, the return value will be
                        the same as that returned by
                        `EventSinkPipelineEnd`.

The iterator returned is a pointer like object.
                        The objects it points to are
                        `std::pair<std::string, CEventSink*>`
                        where the first element of the pair is the name of the event
                        sink pointed to by the second element of the pair.

`   CEventSinkPipeline::EventSinkIterator  FindEventSink(CEventSink&  sink);`Returns an iterator 'pointing' to the event sink
                        pipeline element whose reference is p[assed in
                        to to the method as `sink`

`   void  InsertEventSink( CEventSink&  sink,  CEventSinkPipeline::EventSinkIterator  here, const  char*  name = 0);`Adds the event sink `sink` to the
                        event sink pipeline prior to the position indicated
                        by `here`, an iterator.
                        If not a null pointer, the parameter `name`
                        is used to name the pipeline element.  Otherwise
                        a unique name is assigned to the element.

`   CEventSink*  RemoveEventSink( std::string  name);`Removes an event sink named `name`
                        from the event sink pipeline.  A pointer to the
                        removed sink is returned on success.  If no
                        event sink with `name` exists,
                        a null pointer is returned.

`   CEventSink*  RemoveEventSink( CEventSinkPipeline::EventSinkIterator  here);`Removes an event sink from the pipeline given an
                        iterator that points to the std::pair containing the
                        specific sink.  Returns a pointer to the event sink
                        that was removed.

`   Int_t  EventSinkPipelineSize();`Returns the number of elements in the event sink pipeline.
                        Just after SpecTcl starts, this will return
                        at least 1
                        as the event sink pipeline is initialized with a
                        `CHistogrammer` as an event
                        sink.

`   CEventSinkPipeline::EventSinkIterator  EventSinkPipelineBegin();`, `   CEventSinkPipeline::EventSinkIterator  EventSinkPipelineEnd();`These methods support iteration over the event sink
                        pipeline.  `EventSinkPipelineBegin`
                        returns an iterator that 'points' to the first item
                        in the pipeline (usually the histogrammer).

`CEventSinkPipeline::EventSinkIterator`
                        objects can be thought of as pointers.  They point to
                        a
                        `std::pair<std::string, CEvetnSink*>`.
                        The first element of that pair is the name assigned to the
                        event sink.  The second element is a pointer to an
                        event sink that was assigned that name.

`CEventSinkPipeline::EventSinkIterator`
                        objects can be incremented.  Each increment points
                        the iterator to the next object in the pipeline.
                        Incrementing an iterator that points to the last item
                        in the pipeline makes it equal to the object
                        returned by
                        `EventSinkPipelineEnd`.

Filters are the most common type of non histogrammer elements
            in the event processing pipeline.  SpecTcl has command line
            mechanisms for creating, configuring and enabling filters.
            The next several methods provide the same functionality for
            C++ extensions to SpecTcl as well as providing a method for
            extending the set of output formats supported by standard filters.

Naturally, for special needs, programmers can extend the
            `CGatedEventFilter` class and use
            the resulting filters in these API elements.



`   void   createFilter( std::string  name,  CGatedEventFilter*  pFilter);`Adds a new filter, `pFilter` to the
                        event sink pipeline.  The filter will be given the name
                        `name`.  The filter is also
                        entered into the filter dictionary so that it is
                        visible to and can be manipulated with SpecTcl
                        commands.

`   CGatedEventFilter*  findFilter( std::string  name);`Locates returns a pointer to the event filter
                        `name`.  If no filter with that
                        name has been created a null pointer is returned.

`   bool   filterExists( CGatedEventFilter*  pFilter);`Given a pointer to an event filter `pFilter`,
                        determines if a filter with the same address exists in
                        the filter dictionary.  Returns true
                        if so and false if not.

`   void   deleteFilter( CGatedEventFilter*  pFilter);`Removes the filter pointed to by `pFilter`
                        from the filter dictionary.  If `pFilter`
                        is not in the filter dictionary, no action is taken.

`   void   deleteFilter( std::string  filterName);`Removes a filter from the filter dictionary.    If the
                        filter is not in the dictionary, this is a silent No-op.

Neither this method, nor the previous one actually delete
                        the storage associated with a filter, they only
                        remove it from the filter dictionary.  To perform
                        a full deletion would require something like:

<a name="AEN2247"></a>```
                            
// Delete by pointer.
                            
CGatedFilter* pFilter=makeSomeFilter();
...
SpecTcl* pApi = SpecTcl::getInstance();
pApi->deleteFilter(pFilter);
delete pFilter;

// Delete by name with full deletion.

CGatedFilter *pSomeFilter = pApi->findFilter("someName");
if (pSomeFilter) {
    pApi->deleteFilter("someName");
    delete pSomeFilter;
}
                        
```

`   void   addFilterOutputFormat( CFilterOutputStageCreator&  creator);`Adds a new filter output format to the filter subsystem.
                        `creator`, when given its output
                        format name, recognizes it and returns the appropriate
                        output formatter.  The programming guide provides
                        a worked example that shows how to add filter
                        formats to the system.

The remainder of the API are miscellaneous methods that don't really
            fit well into any of the method categories above.



`   void  AddSpectrumFormatter( std::string  name,  CSpectrumFormatter&  formatter);`Associates the `formatter` with
                        outputting spectra (via the **swrite** command)
                        for the format type `name`.
                        The actual `formatter` must be in scope
                        for the lifetime of SpecTcl.   Therefore it's recommended
                        that it either be statically allocated at a file scope
                        or alternatively dynamically allocated via new
                        and never destroyed with delete.

`   CTCLInterpreter*  getInterpreter();`Returns a pointer to the object encapsulated
                        Tcl interpreter that SpecTcl is using to execute its
                        commands.  This can be used to add commands to SpecTcl,
                        or anything else that may require a Tcl interpreter.
                        See the Tcl++ section of this manual for more information
                        about how to use this and other classes in the
                        Tcl++ C++ encapsulation of libTcl.

`   CHistogrammer* GetHistogrammer();`Returns a pointer to SpecTcl's histogrammer object.
                        Note that most of the things you'd want to do with the
                        `CHistogrammer` are possible
                        directly from the API methods above.  Those are
                        considered 'sacred with respect to modification' while
                        the methods of the histogrammer can be modified in
                        function and signature.

`   CTclAnalyzer*  GetAnalyzer();`Returns a pointer to the current SpecTcl analyzer.
                        The `CAnalyzer` is the method
                        that directs the flow of control within SpecTcl's analysis
                        of data.  Normally, the SpecTcl analyzer is actually a
                        `CTclAnalyzer` object
                        (see TCLAnalyzer.h for the class
                        definition).

`   CEventSinkPipeline*  GetEventSinkPipeline();`Returns a pointer to the event sink pipeline object.
                        Note that other methods in this API provide essentially
                        all of the operations you'll need to perform on this object.

`   CDisplayInterface*  GetDisplayInterface();`SpecTcl 5.0 decouples SpecTcl from its traditional
                        displayer (Xamine), and provides an new Root based
                        displayer (Display).  The interaction between the
                        displayer and SpecTcl is mediate by a
                        `CDisplayerInterface` object
                        that is specific to the displayer type.  This
                        method obtains a pointer to the specific
                        displayer interface object in use.

I anticipate that later in the development of SpecTcl 5,
                        we'll see the `SpecTcl` class
                        augmented to provide a stable API to the displayer.

`   void SetDisplayInterface CDisplayInterface& rInterface();`Provides a new display interface to SpecTcl;
                        `rInterface`.

`   std::vector<UInt_t>   parameterIds( std::vector<std::string>  names);`Given a list of parameter `names`,
                        Returns a vector of the parameter ids associated with those
                        names.  The 0'th element of the result is the
                        id of the 0'th element of `names`
                        and so on.

If any of the parameters in `names`
                        does not exist a `std::vector<std::string>::iterator`
                        exception is thrown which 'points' to the element of
                        `names` that failed its lookup.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| SpecTcl | Up | Tree Parameter, Tree Variable API |
