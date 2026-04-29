|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="provider3_start"></a>start

<a name="AEN55096"></a>## Name

start -- Start a data source

<a name="AEN55099"></a>## Synopsis

**::*providerName*::start *param-dict*
**

<a name="AEN55104"></a>## DESCRIPTION

Starts a data source for the provider.   The
            `param-dict` parameter is a Tcl
            [[dict]].  The keys for the dict are the
            same as the keys for the dict returned from
            [[r55059]].
            Key values are the parameter values.  An additional key
            sourceid is always added to this dict and it
            represents a unique identifier that will be used
            to refer to this data source from now on.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| parameters | Up | check |
