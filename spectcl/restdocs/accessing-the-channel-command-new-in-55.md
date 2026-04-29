|  |  |  |
| --- | --- | --- |
| SpecTcl REST plugin |
| Prev | Chapter 3. REST requests supported. | Next |


---

# <a name="AEN1042"></a>3.13. Accessing the channel command (new in 5.5)

Spectrum channel values can be inspected or set using this interface
                Note that the spectrum contents interface may be a more
                performant method to get bulk spectrum information.

URLS of the type below can set the value of a spectrum channel:

<a name="AEN1046"></a>**http://host:port/spectcl/channel/set?spectrum=name&xchannel=x&value=value[&ychannel=y]
                    **

The spectrum query parameter specifies
                the name of the spectrum to operate on.
                xchannel specifies the x channel number.
                If the spectrum selected is a 2-d spectrum,
                ychannel is needed to  specify the y channel.
                Regardless, value specifies the value
                to stuff into that spectrum channel.

Note that the *channel* coordinates are
                specified, not real coordinates.

<a name="AEN1057"></a>**http://host:port/spectcl/channel/get?spectrum=name&xchannel=x[&ychannel=y]
                **

URLs of the form above, return the value of a channel of a spectrum
                in the detail attribute of the reply object.
                The query values spectrum and
                xchannel specify the spectrum name and
                x channel to fetch. If the spectrum is 2d, an additional
                ychannel query parameter is required to
                specify the y channel.

Note again, that the xchannel and
                ychannel coordinates are in spectrum coordinate
                units not real coordinates.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| REST interface for the fold command (new in 5.5) | Up | Projecting spectra (new in 5.5) |
