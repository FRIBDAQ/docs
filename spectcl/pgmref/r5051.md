|  |  |  |
| --- | --- | --- |
| SpecTcl Programming Reference. |
| Prev |  | Next |


---

# <a name="manpage.CTCLObjectProcessor"></a>CTCLObjectProcessor

<a name="AEN5055"></a>## Name

CTCLObjectProcessor -- 
            Abstract base class to encapsulate the Tcl object command interface exposed by
            `Tcl_CreateObjCommand`.

<a name="AEN5059"></a>## Synopsis

```
#include <TCLObjectProcessor.h>
...
class CTCLObjectProcessor : public CTCLInterpreterObject
{
public:
  CTCLObjectProcessor(CTCLInterpreter& interp,
                      std::string      name,
                      bool             registerMe=true);
  virtual ~CTCLObjectProcessor();

  void Register();              // Register command on the interpreter.
  void unregister();            // Unregister command from the interp.
  std::string getName() const;  // Return the name of the object.
  Tcl_CmdInfo getInfo() const;  // Return info about the command.

protected:
  virtual int operator()(CTCLInterpreter& interp,
                         std::vector<CTCLObject>& objv) = 0;
  virtual void onUnregister();

protected:
  void bindAll(CTCLInterpreter& interp, std::vector<CTCLObject>& objv);
  void requireAtLeast(std::vector>CTCLObject<& objv, unsigned n, const char* msg=0) const;
  void requireAtMost(std::vector<CTCLObject>& objv, unsigned n, const char* msg=0) const;
  void requireExactly(std::vector<CTCLObject>& objv, unsigned n, const char* msg=0) const;



};

    
```

<a name="AEN5061"></a>## DESCRIPTION

Tcl supports the addition of commands to the interpreter.  `CTCLObjectProcessor`
            supports an object oriented encapsulation of this part of the API.
            To add a command to an interpreter, write a subclass of
            `CTCLObjectProcessor`.  This subclass should override
            `operator()`, and optionally `onUnregister`.
            to implement the desired behavior for the new command.

Create an instance of this new class and invoke its
            `Register`
            member to add it to the interpreter onto which it is bound.  Whenever a
            script executes the new command that object's
            `operator()` is invoked to process the command.
            If the interpreter is destroyed, or if the command is ever unregistered,
            the `onUnregister` function is called to perform any
            required global cleanup.

<a name="AEN5072"></a>## METHODS



```
CTCLObjectProcessor
```


Constructs a new command processor.  `interp` is the
            interpreter on which the command will be registered when the
            `Register` member is invoked.
            `name` is the name of the command.
            If `registerMe` is not supplied or is supplied but is
            true, the command will be registered as part of the construction process.
            If `registerMe` is supplied and is false,
            the command is not immediately added, and `Register` must
            be called later to incorporate it into the interpreter.



```
Register
```


`Register` incorporates the command into the
            interpreter.  If the command is already registered, a
            `CStateException` is thrown.

`unRegister` removes the command from the interpreter.
            This causes `onUnregister` to be called.
            if the command is registered at destruction time, destruction implies a call
            to `unRegister` (and therefore `onUnregister`).



```
getName
```


`getName` returns the name of the command
            that will invoke this object's `operator()`.
            If the command has been registered, and subsequently renamed at the
            script level, this function will reflect the rename.

`getInfo` returns information about the command
            see `Tcl_GetCommandInfo` for more information about
            what is returned and what it means.



```
operator()
```


This pure virtual function must be overridden in concrete object command processors.
            The function is called to execute the command that this object is performing.
            `interp` provides a reference to the interpreter on which
            the command is being run. `objv` is a reference to a
            std::vector<CTCLObject>.
            Each element of `objv` is a `CTCLObject`
            containing a word of the command line that invoked us.

The function should return TCL_OK on success and
            TCL_ERROR on failure.  Other return values are possible
            for e.g. commands that implement new control structures however this is beyond
            the scope of this manpage.  If the command processor wants to make a result
            available to the interpreter, it can create a `CTCLResult`
            object, fill it in and commit it.



```
virtual void onUnregister();
        
```


This function is called when the interpreter is being destroyed or if the
            command is being unregistered either due to object destruction or a call to
            `unregister`.  The default behavior is to do nothing, but
            this can be overidden in your derived class if desired.

```
void bindAll(CTCLInterpreter& interp, std::vector<CTCLObject>& objv);            
        
```

This is a convenience method for derived classes.  It binds the
            interpreter to all of the elements of the
            `objv` vector.  Several of the methods of
            `CTCLObject` require that an interpreter
            be bound.

```
void requireAtLeast(std::vector>CTCLObject<& objv, unsigned n, const char* msg=0) const;            
        
```

Utility method.  Throws an `std::string`
            exception if the `objv` vector does
            not have at least `n` elements.
            If `msg` is provided (non Null pointer),
            that string is incorporated in the exception string.

```
void requireAtMost(std::vector<CTCLObject>& objv, unsigned n, const char* msg=0) const;            
        
```

If `objv` has more than
            `n` elements, an
            `std::string` exception is thrown.  If
            `msg` is provided (not a null
            pointer) it is incorprorated into the exception string.

```
void requireExactly(std::vector<CTCLObject>& objv, unsigned n, const char* msg=0) const;            
        
```

If the `objv` vector does not have exactly
            `n` elements, an `std::string`
            exception is thrown.  If `msg` is supplied
            (not a null pointer), the exception string will incorporate it.

<a name="AEN5163"></a>## SEE ALSO

CTCLCompatibilityProcessor(3),
CTCLInterpreter(3),
CTCLInterpreterObject(3),
CTCLObject(3),
CTCLProcessor(3),
CTCLResult(3),
Tcl_CreateObjCommand(3tcl),
Tcl_GetCommandInfo(3tcl)

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CTCLException | Up | CTCLProcessor |
