|  |  |  |
| --- | --- | --- |
| SpecTcl REST plugin |
| Prev | Chapter 3. REST requests supported. | Next |


---

# <a name="AEN278"></a>3.3. spectrum requests

The spectrum service group provides
                operations that revolve around spectra in SpecTcl.
                This service group allows you to request information
                about spectra, create and delete spectra.

The base URL for this service group is

<a name="AEN283"></a>```
http://host.name:port-num/spectcl/spectrum                    
                
```

## <a name="AEN286"></a>3.3.1. list

Produces information about the spectra whose
                    names match a pattern with glob wildcards characters.
                    The filter optional parameter
                    provides the value of this pattern.  If not
                    supplied it defaults to *
                    which matches all spectra.

The detail attribute of the
                    returned object is an array of objects, one object
                    for each matching spectrum.  Each of these objects
                    has the following fields that, taken together, describe
                    the spectrum:



nameThe spectrum name.

typeThe SpecTcl spectrum type code.

paramsThe SpecTcl spectrum parameter definitions.
                                This is provided as an array of strings.

axesThis is an array of objects that
                                describe the SpecTcl axes.  Each object
                                has the attributes low for
                                the axis low limit, high
                                for the axis high limit and bins
                                for the number of bins on that axis.

chantypeThe SpecTcl channel type code (e.g. long).

## <a name="AEN323"></a>3.3.2. delete

Deletes a single spectrum.  The name
                    parameter provides the name of the spectrum to delete.

On success the detail field is empty.
                    The non success returns include:

**missing parameter. **
                        The name parameter was not supplied.

**not found. **
                        There was no spectrum with the name provided.

**command failed. **
                        The **spectrum -delete** command failed.
                        detail contains the error message returned
                        by the command.

## <a name="AEN341"></a>3.3.3. create

Creates a new spectrum.  The  spectrumto be created is
                    defined by the query parameters, most of which are mandatory:



name (mandatory)The name of the new spectrum.  This must not
                                be the name of an existing spectrum.

type (mandatory)The spectrum type code e.g. 1
                                for a 1-d spectrum.

parameters (mandatory)The parameters expressed as a space separated list.

axes (mandatory)The axis specifications.  This is a space separated
                                list of SpecTcl axis specifications e.g.:
                                {0 1023 100} {0 1023 200}.

chantype (optional)The spectrum channel type, defaults to
                                long.

On success, the detail field of the
                        returned objexct is empty.  Several types of failures are
                        directly tested for:



missing parameterA mandatory parameter was not supplied.

command failedThe **spectrum -create**
                                command failed.  detail
                                is the error message from that command.

## <a name="AEN387"></a>3.3.4. clear

Clears the counts in a set of spectra. The
                    pattern parameter supplies
                    a glob patternt hat the cleared spectra match.
                    pattern defaults to *
                    which clears all spectra

This operation has no failure returns.  The worst thing
                    it can do is to clear nothing (no matching patter).
                    The detail attribute of the returned
                    objetct is also empty

## <a name="AEN395"></a>3.3.5. contents

Returns the contents of the a spectrum.  The contents of a
                    spectrum are sufficient to reconstruct the spectrum channels
                    and overflow statistics.
                    The only parameter is the mandatory name
                    parameter which is the name of the spectrum to return.

There are some significant differences in what can be returned.
                    These differences depend on the underlyng spectrum type
                    (1 or 2d) and the version of SpecTcl the REST server is running
                    on (4.0 or earlier).

Prior to SpecTcl 4.0, spectra did not maintain over/undeflow
                    statistics.  The REST interface for those version of SpecTcl
                    produced an array of channel objects for the channels with
                    non-zero counts as the value of the detail
                    attribute:

Channel objects have the following attributes:



xThe X channel number.

y (2-d spectra only)The Y channel number.

vThe number of counts at that channel.

Beginning with SpecTcl version 4.0, the detail
                    attribute became an object with the attributes
                    channels and statistics.
                    The channels attribute contains the array
                    of channel objects and the statistics attribute
                    contains an object that describes the over/underflow statistics
                    for the spectrum.  Its attributes are:



xunderflowThe number of times an X parameter value was below
                                the X axis low limit.

yunderflow (2-d only)The numer of times a Y parameter value was below the
                                Y axis low limit.

xoverflowThe number of times an x parameter was above the
                                X axis high limit.

yoverflow (2-d only)The number of times a Y parameter value was above
                                the Y axis high limit.

Two optimizations are performed.  Channel objects are only
                    present for non-zerof channels.  2d spectra may be emitted with
                    the Content-encoding deflate.  In that
                    case the special header Uncompressed-Length
                    provides the number of bytes required to hold the uncompressed
                    JSON after defation.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Parameter requests | Up | gate requests |
