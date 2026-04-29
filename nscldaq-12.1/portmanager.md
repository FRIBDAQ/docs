|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="python3_PortManager"></a>PortManager

<a name="AEN84191"></a>## Name

PortManager -- Python bindings to port manager

<a name="AEN84194"></a>## Synopsis

**from nscldaq.PortManager import PortManager
          **

**pm = PortManager(host, port=30000)
            **

**port = pm.getPort(servicename)
            **

**portinfo = pm.listPorts()
            **

**portinfo = pm.find(key=value,...)
            **

<a name="AEN84205"></a>## DESCRIPTION

Provides a python interface to the port allocator.  The port allocator
            is a service that runs on NSCLDAQ that allows servicers to obtain a
            listen port from a pool of dynamically allocated ports.  The service
            is then advertised by the port manager so that clients can locate and
            connect to the service.

<a name="AEN84208"></a>## METHODS



<a name="AEN84213"></a>`PortManager(string host, int    port);`

Constructs a `PortManager`
                            object
                            and returns a reference to it.  `PortManager`
                            objects represent connections to port manager
                            servers.  `host` is the host
                            on which the port manager server is running
                            and `port` is the port
                            on which the port manager is listening for
                            connections.  By default (and if this parameter
                            is not supplied), the `port`
                            is 30000, which is, by default
                            where the NSCL port manager listens.

The `host` parameter is a
                            string that can either be the DNS name of the
                            host or the IP address (dotted form) of that
                            host.

` int getPort(string servicename);`This method of a port manager object interacts
                            with a local port manager (the host specified
                            whenthe object was created must be
                            localhost) to allocate a port
                            and associated it with a service specification.

Service specification consist of two parts, a
                            service name, specified by the
                            `servicname` parameter
                            and the name of the user running the server,
                            specified automatically by the `getPort`
                            method.

On success, the method returns the integer
                            allocated port number.  On failure, an exception
                            raised.  The exception can be a
                            `RuntimeError`, if the
                            server reported an error condition, or any
                            other error the socket calls might return.

In the event of a `RuntimeError`
                            exception, the text of the exception is the
                            error message string returned by the server.
                            Regardless, once an error exception has been
                            raised, the caller should assume that all
                            previously allocated services have been released
                            and that the connection to the port manager
                            object has been terminated.  The calling program
                            should allow the port manager object to be
                            garbage collected, and should not attempt to make
                            use of the object again.

` list of dicts listPorts();`Obtains a list of the ports the server has allocated.
                            This is most often done to determine which port to
                            perform a socket.connect call
                            on to connect to a specific service.
                            See, however the `find`
                            which performs some filtering of the full port
                            list obtained via `listPorts`

The result is a list of dicts.  The
                            service key of each dict contains
                            the name of the service, while the user
                            key the user that is running the server.  The
                            port key contains the port itself.

` list of dicts find(keyword/value list **criteria);`First performs a `listPorts`
                            call and then filters the data returned by that
                            call using the keyword value pairs in the
                            `**criteria`.

Keywords are applied cumulatively and in
                            the following order:

service the value of this
                            keyword is a service name that must be
                            exactly matched to allow a port definition
                            to survive the filter.

beginswith
                            is a prefix to the service name.  Only services
                            whose names begin with this value survive
                            the filtering.  The motivation for this criterion
                            is that if a user starts up more than one service
                            with the same name, the port manager silently appends
                            _n to the name, where n is a
                            unique integer (e.g. myService,
                            myService_1).  The
                            prefix criterion allows
                            you to list all instances of a single service
                            run on a node by a user.

user Filters the data to
                            match only those services run by a specific
                            user.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| LogBook.Note | Up | pidtocommand |
