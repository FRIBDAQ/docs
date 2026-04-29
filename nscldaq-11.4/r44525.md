|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="daq3.ctcpnosuchhost"></a>CTCPNoSuchHost

<a name="AEN44539"></a>## Name

CTCPNoSuchHost -- CTCPNoSuchHost

<a name="AEN44542"></a>## Synopsis

```
CTCPNoSuchHost
```

<a name="AEN44586"></a>## DESCRIPTION

An exception class that is thrown when a
        `CSocket::Connect` is
        done to a host that demonstrably does not exist.  This may be because the
        host provided to `CSocket::Connect` is incorrect or
        because the host is not currently alive.

<a name="AEN44591"></a>## METHODS



`  CTCPNoSuchHost(const  std::string& hostname, const  std::string& Doing);`Constructs the exception. `hostname`
                    is the DNS name or dotted IP address of the host that
                    does not exist.  `Doing` is a string
                    that describes what the library was doing when this
                    object was constructed/thrown.

`  const int  gethErrno();`TCP/IP networking reports some errors via the
                    `h_errno` global variable.  The value of
                    this variable is captured and stored by the exception's
                    constructor.  This method returns the value of
                    `h_errno` as it was at construction time.

[http://linux.die.net/man/3/h_errno](http://linux.die.net/man/3/h_errno)
                    contains a description of the values of
                    `h_errno`.

`  const std::string  getHost();`Returns the host string passed in to the contructor.  Typically
                    this will designate the host to which a connection could
                    not be formed.

` virtual const  const char *   ReasonText ();`Returns a human readable error message that desribes
                    the failure.

` virtual  const int ReasonCode();`Overrides the base class's method and
                    returns the saved `h_errno`

<a name="AEN44656"></a>## SEE ALSO

[[r43320]]

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CTCPConnectionLost | Up | CTCPNoSuchService |
