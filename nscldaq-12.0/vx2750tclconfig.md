|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN65374"></a>VX2750TclConfig

<a name="AEN65378"></a>## Name

VX2750TclConfig -- Tcl scripted configuration.

<a name="AEN65381"></a>## Synopsis

```
#include <VX2750TclConfig.h>
namespace caen_nscldaq {
class VX2750TclConfig : public ::CTCLObjectProcessor
{
public:
    VX2750TclConfig(CTCLInterpreter& interp, const char* pName);
    
    int operator()(CTCLInterpreter& interp, std::vector<CTCLObject>& objv);
    VX2750PHAModuleConfiguration* getModule(const char* pName);
    std::vector<std::string< listModules();
  
};
}
                    
```

<a name="AEN65383"></a>## DESCRIPTION

Provides a Tcl language extension for gathering named
                        module configurations for CAEN Nextgen ADC's running
                        the DPP-PHA firmware.

The extension adds a single command which is a command
                        ensemble.   In Tcl parlance, a command ensemble is a
                        command whose operation depends on its first parameter,
                        known as a subcommand, which is also called an
                        ensemble command.

The command ensemble's command name is determined
                        at construction time.  Ensemble subcommands provide
                        for the creation and deletion of named module configurations,
                        the configuration and interrogation of existing named
                        configurations and the ability to determine the
                        configurations that have been defined.

The programmatic interface provides for construction,
                        which registers the command with the interpreter in such
                        a way that the `operator()` method
                        of the object is invoked properly when the base command
                        is encountered in a script by the interpreter.

Programs using this may also look up a configuration by its
                        name and obtain a list of the names of configurations.

For a normal use of this in context, see the
                        `TclConfiguredReadout` class
                        and documentation.

<a name="AEN65393"></a>## METHODS



`  VX2750TclConfig(CTCLInterpreter& interp,  const char*  pName);`Constructs new object.  `interp`
                                is a reference to an object wrapped Tcl interpreter
                                on which the base command will be registered.
                                `pName` provides the ensemble
                                base command.

By object wrapped we mean an Tcl_Interp*
                                that's been wrapped in the Tcl++ C++ Tcl interface
                                library.   See the documentation of
                                Tcl++ for more.

` int  operator()(CTCLInterpreter& interp, std::vector<CTCLObject>&  objv);`This method is automatically called by the
                                Tcl interpreter `interp` when
                                that interpreter has been asked to execute the
                                command passedto the constructor.
                                The command words (including the base command)
                                are passed in the `objv`
                                parameter.

On success, the method will return
                                TCL_OK, otherwise
                                TCL_ERROR.  The interpreter result
                                will generally be error information if
                                TCL_ERRROR is returned
                                and depends on the enemble command if
                                TCL_OK is returned.

` VX2750PHAModuleConfiguration*  getModule(const char*  pName);`Either returns a pointer to the configuration
                                that is associated with `pName`
                                or throws a string exception.  The
                                command retains ownership of the object. However
                                the configuration can subsequently be manipulated
                                by the caller in any desired way.

If `pName` does not refer
                                to a configuration, a `std::string`
                                exception is thrown.

` std::vector<std::string>  listModules();`Returns a (possibly empty) vector of configuration
                                names.

<a name="AEN65454"></a>## ENSEMBLE COMMANDS

Constructing provides a base command.
                        In the documentation below the string
                        xxxx is meant to be that base command.
                        Subcommands
                        determine what that base command does and are as follows:



** xxxx create *name*
**

Creates a new configuration; `name`.
                                If `name` already is assigned
                                to a configuration, TCL_ERROR
                                is returned with the result set to
                                Duplicate configuration name

**xxxx config *name parname value ...*
**

Changes the configuration for
                                `name`.  The pairs that follow
                                are configuration option names and their new
                                proposed values.

If `name` does not represent
                                a configuration TCL_ERROR is
                                returned are are any errors from the
                                underlying configuration attempt
                                (e.g. no such configuration parameter or value
                                validation failure).

**xxxx cget *name paramname ...*
**

Retrieves the textual representation of the parameter
                                names from the configuration named
                                `name`.  For each parameter
                                name  specified a two elemenbt list is added to the
                                result.

The parameter names and values are documented in the
                                manpage for `VX2750PhaConfiguration`

**xxxx delete *name*
**

Deletes the configuration  named
                                `name`.

**xxxx list 
                              **

Returns the list of existing module
                                configuration names as the result.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| VX2750PHAModuleConfiguration | Up | TclConfiguredReadout |
