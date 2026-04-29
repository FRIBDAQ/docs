|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.CPortManager"></a>CPortManager

<a name="AEN23769"></a>## Name

CPortManager -- Provide a C++ interface to the server port manager daemon.

<a name="AEN23772"></a>## Synopsis

```
#include <config.h>
#include <CPortManager.h>
#include <CPortManagerException.h>
         
```

```
CPortManager
```

<a name="AEN23801"></a>## Description

`CPortManager`
       provides  a  C++ application programming interface into the NSCL
       port manager server.  This class serves as a proxy for communication with port
       management  servers.  Once you have created a
       `CPortManager` object, you can use
       it to allocate ports (if the server is local), and to list port usage  of  any
       server on the network.

Note  that  members of this class can throw exceptions of type
       `CPortManagerException`.
        See the [[r23912]] for
        more informationa bout that.

To include the headers required you, or the Makefile skeleton you are using must
            have added the include subdirectory ofthe NSCLDAQ installation
            directory tree to the include paths for the compile e.g.:
            -I/usr/opt/daq/current/include.

To link you must include the NSCL DAQ lib subdirectory in the library search path,
            link in the library and ensure that the shared library can be found at load time.
            For example:

```
-L/usr/opt/daq/current/lib \
-lPortManager \
-Wl,"-rpath=/usr/opt/daq/current/lib"
            
```

<a name="AEN23814"></a>## Public member functions

`  CPortManager(std::string host = string("localhost"));`Constructs a port manager interface object.  The object connects to the
              port manager running on the host `host`, using the
                default port (30000) to form the connection.  If the
                `host` parameter is omitted, it defaults to
                localhost

`  CPortManager(std::string host, int Port);`Constructs a port manager interfaceobject.  The object connects
                to the host manager running on `host` via the
                connection port `Port`.

` int allocatePort(std::string application);`Allocates a port from the port manager.  On success the return value is the
                port number allocated in local machine byte order.  Note that when interacting
                with the network functions, in general, this will have to be converted to network
                byte ordering.

Once the port is allocated, it remains allocated until the program exits.
                This is because a connection will be held with the port manager and cannot
                be closed by the user.

If a port could not be allocated (e.g. all are in use or the port manager could
                not be contacted, a `CPortManagerException` described
                in "Types and public data" below and completely in
                [[r23912]].

` std::vector<portInfo> getPortUsage();`Returns a vector of portInfo structs that describes
                the current port allocations of the port allocator.  The most common use case
                for this is to locate a specific service offered by a remote port manager.

If the interaction with the server failed,
                a `CPortManagerException` described
                in "Types and public data" below and completely in
                [[r23912]].

<a name="AEN23858"></a>## Types and public data

The set of port allocations is described by an STL vector of
            portInfo structs.  The `std::vector`
            is described in any C++ reference that contains a description of the Standard
            Template Library (STL).

portInfo structs have the following fields:

**Type: **int

**Name: **`s_Port`

**Description: **
                        
                            The port number that this object describes. The port number is
                            provided in the byte order of the local system.   Note that when used
                            to provide a port number to Unix/Linux network functions in general
                            this number will have to be converted to network byte order.

**Type: **std::string

**Name: **`s_Application`

**Description: **
                        
                            The name of the application that requested this port.  The application
                            name represents some service that is being offered.  Usually (but not
                            always), the application name and the `s_User` fields
                            together are unique  system wide.

**Type: **std::string

**Name: **`s_User`

**Description: **
                        
                            The name of the user that was running the application that reserved
                            this port.  In the event that several users have run the same
                            application on a single system, this identifies which user ran
                            the application that requested this port.


`CPortManagerException` objects are thrown in most cases
            the library encounters an exception.

<a name="AEN23890"></a>## Exceptions

The `CPortManagerException` is thrown to inform the
            program of most errors dected by this API.  For more information about
            this exception, see:  [[r23912]].

<a name="AEN23895"></a>## EXAMPLES

Allocates a port to MyApplication

<a name="AEN23899"></a>**Example 1. Allocating a port with the port manager**

```
…
CPortManager pm;
int port;
try {
 port = pm.allocatePort("MyApplication");
 ListenOnPort(port);                      // Not shown for brevity
}
catch (CPortManagerException& error) {
 cerr << "Could not allocate a port: " << error << endl;
 exit(-1);
}
…

            
```

Lists to cout the  port allocations on the system:
            ahost.nscl.msuedu

<a name="AEN23903"></a>**Example 2. Listing the port allocatiosn on a system.**

```
    …
   CPortManager pm("ahost.nscl.msu.edu");
   vector<CPortManager::portInfo> info = pm.getPortUsage();
   for(int i =0; i < info.size(); i++) {
      cout << "Port " << info.s_Port
           << " allocated to " << info.s_Application
           << " run by " << info.s_User << endl;
   }
    …

            
```

<a name="AEN23906"></a>## SEE ALSO

[[r68753]],
            [[r23912]],
            [[r15119]]

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CEventOrderClient | Up | CPortManagerException |
