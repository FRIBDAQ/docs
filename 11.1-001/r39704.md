|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="daq3.ctcpconnectionfailed"></a>CTCPConnectionFailed

<a name="AEN39716"></a>## Name

CTCPConnectionFailed -- Exception thrown for TCP/IP connection failures.

<a name="AEN39719"></a>## Synopsis

```
CTCPConnectionFailed
```

<a name="AEN39755"></a>## DESCRIPTION

This class is an exception that is thrown when `CSocket::Connect`
        fails to connect to a peer host/port pair.

<a name="AEN39759"></a>## METHODS



`  CTCPConnectionFailed(const std::string&  host, const  std::string&  service, const  char*    pDoing);`Constructs the exception object.
                    `host` is either a DNS fully qualified
                    host name or a string containing a dotted IP address.
                    `host` is the host to which the connection
                    request failed.

`service` is either a service name
                    string (in e.g. /etc/hosts) or the string
                    representation of an integer service port number.
                    `service` represents the service in
                    `host` to which the connection operation
                    failed.

`pDoing` is a string that describes
                    what the library was doing at the time of the failure e.g.
                    CSocket::Connect client connect(2) failed.

`  const std::string  getHost();`Returns the name or dotted IP address of the host passed in
                    to the constructor.

`  const std::string  getService();`Returns the service string used to construct the object.

` virtual const  const char*  ReasonText();`Returns human readable text that describes why the
                    exception was created/thrown.

<a name="AEN39820"></a>## SEE ALSO

[[r38735]]

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CTCPBadSocketState | Up | CTCPConnectionLost |
