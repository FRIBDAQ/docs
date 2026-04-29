|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.CTCLApplication"></a>CTCLApplication 3

<a name="AEN56479"></a>## Name

CTCLApplication -- 
            Base class for TCL/Tk applications.

<a name="AEN56482"></a>## Synopsis

```
#include <tcl.h>
#include <TCLApplication.h>
...
class CTCLApplication  : public CTCLInterpreterObject
{
public:
  CTCLApplication ();
  ~CTCLApplication ( );
  virtual   int operator() ()  =0;
  void      getProgramArguments(int&, char**& argv);
};
        
```

<a name="AEN56484"></a>## DESCRIPTION

`CTCLApplication` is an abstract base class
            that facilitates the creation of applications that extend the
            Tcl interpreter.  The `main program' of SpecTcl is derived from
            this class, for example.

Initializing a Tcl application generallly consists of a bunch
            of boilerplate that initializes the interpreter, and then a bunch
            of application specific code to register extensions to the interpreter.
            `CTCLApplication`
            provides the main boilerplate.  It is expected that you
            derive a class from
            `CTCLApplication`
            Implement `operator()` to register
            application specific commands, and then create exactly one
            instance of your application class named, and a global pointer
            to that object named gpTCLApplication.

For example, suppose you have created a class named MyTclApp:

<a name="AEN56493"></a>```
// This code is at the global level:
...
MyTclApp app;                              // Makes an instance of this
CTCLApplication* gpTCLApplication = &app;  // Pointer expected by framework.
...
            
```


            Will ensure that the `operator()` of your
            application object will be called with the interpreter already
            initialized.

<a name="AEN56496"></a>## METHODS

int `operator()`()

This function is pure virtual and must be overridden by your
            derived class.  `operator()` is expected to
            install all required extensions to the interprter and return to it
            to start the main event loop.  The return value from this should be
            TCL_OK if the application was successfully initialized
            or TCL_ERROR if the program encountered an error that
            should prevent the interpreter main loop from starting

` void getProgramArgs(int& argc, char**& argv);`Provides a mechanism for the concrete class to get the program
            arguments. This allows the program arguments to be parsed for
            application specific switches and arguments.

<a name="AEN56515"></a>## SEE ALSO

CTCLInterpreter, CTCLInterpreterObject, CTCLObjectProcessor, CTCLVariable

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CTCPNoSuchService | Up | CTCLException |
