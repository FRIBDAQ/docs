|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.CTCLTcpServerInstance"></a>CTCLTcpServerInstance

<a name="AEN41181"></a>## Name

CTCLTcpServerInstance -- Channel commander that is a server instance for `CTCLServer`

<a name="AEN41185"></a>## Synopsis

```
#include <CTCLTcpServerInstance.h>
         
```

```
  CTCLTcpServerInstance(CTCLInterpreter* pInterp, Tcl_Channel connection, CTCLServer* pServer);
```

<a name="AEN41215"></a>## Description

Server instance that takes client commands and submits them to
            an interpreter.  The results of each command are sent back to the
            client. At this point the client can only look at the
            result value to determine if there was an error as no error indication
            is passed back.

<a name="AEN41218"></a>## Public member functions

`  CTCLTcpServerInstance(CTCLInterpreter* pInterp, Tcl_Channel connection, CTCLServer* pServer);`Constructs a new server instance.
                `pInterp` is the interpreter to which
                commands should be directed.
                `connection` is the Tcl_Channel
                that represents the Tcp/IP connection to the client.
                `pServer` is the TCL server object
                that starts us.  That server's
                `instanceExit` member should be called
                to shut down and clean up this object.

` virtual void onEndFile();`Override to end of file handling.  Closes the
                channel and invokes the
                server listener's `instanceExit`
                method to get ourselves deleted.

` virtual void returnResult();`Returns a command result by fetching it from the interpreter
                and sending it back to the client on the socket.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CTCLServer | Up | CTCLObjectPackage |
