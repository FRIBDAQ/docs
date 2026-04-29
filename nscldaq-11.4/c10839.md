|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="chapter.tclplus"></a>Chapter 59. C++ encapsulation of a Tcl API subset

The tclPlus library provides a C++ object oriented
            encapsulation of a large subset of the Tcl application programming
            interface.  This section provides reference material for this class library.

Sections of the NSCLDAQ and SpecTcl products both make extensive use of this
            library.  It is therefore distributed with both prodcuts, from a common source base.
            Therefore, there are two ways to link to this library.
            First, using SpecTcl:

<a name="AEN10843"></a>```
            g++ -o yourprogram yoursources  \
               -L${SPECTCLHOME}/lib -ltclPlus -lException
            
            
```


            where ${SPECTCLHOME} represents the top level director of
            your SpecTcl installation.  At the NSCL, for example, this could be
            /usr/opt/spectcl/3.2
Second, using nscldaq, replace ${SPECTCLHOME} with the top
            level directory of your NSCLDAQ installation, e.g.
            /usr/opt/daq/8.1.

Some brief descriptions of the primary classes in this library follow:

`CTCLApplication`

This is a base class for complete applications that extend the Tcl/Tk
            interpreter.  By appropriately subclassing it you can build your own
            standalong extended Tcl/Tk interpreters.

`CTCLException`

The Tcl/Tk API use return codes to indicate error conditions.  This is
            error prone.  The tclPlus library converts these return codes in to
            thrown exceptions of the type `CTCLException`.
            To handle these exceptions properly requires use of  C++ try/catch blocks.
            A code fragment example of this is provided in the
            `CTCLException`(3) manpage.

`CTCLInterpreter`

The `CTCLInterpreter` object is at the core of the
            library.  It is a wrapping of a Tcl_Interp* along with member
            functions that access many functions that logically operate on a Tcl interpreter.

`CTCLInterpreterObject`

The `CTCLInterpreterObject` wraps objects that
            require an interpreter to function correctly.  It is a base class for
            many of the classes in the library.  It provides common services for those
            objects.

`CTCLList`

In Tcl scripting, lists play a key role in providing a structured
            data type.  The `CTCLList` object can be created
            on a string believed to be a list, and used to split a list into its
            elements or merge a set of words into a list.

`CTCLObject`

Tcl has the philosophy that everything can be treated as if it were a string.
            In older versions of the interpreter, everything *was* a
            string. This led to a great deal of inefficiency converting other data types
            to and from strings.  The Tcl_Obj type was created to reduce this
            inefficiency and to reduce the amount of string copying that was necessary
            to invoke commands.

A Tcl_Obj is an object  that stores the string representation
            and another representation type for a Tcl interpreter entity.  Tcl_Obj
            also provides for object sharing with copy on modify semantics.  This reduces
            much of the string copying overhead that was previously associated with executing
            Tcl interpreter commands.

The `CTCLObject` is a wrappig of a Tcl_Obj
            along with functions that operate on the underlying object.

`CTCLObjectProcessor`

Key to the concept of the Tcl interpreter as an application scripting language
            is the ability to add new commands to the interpreter that are application
            specific.  The `CTCLObjectProcessor` class is an
            abstract base class that, when subclassed and instantiated adds new
            commands to the interpreter.

`CTCLVariable`

The `CTCLVariable` class provides access to
            Tcl script variables.

`CItemConfiguration` and `CConfigurableObject`
        while not actually Tcl objects provide infrastructure that is useful
        in the context of extension to a Tcl interpreter.  Specifically the
        creation and maintanance of commands that generate objects that have
        some configuration associated with them.  Configuration is expressed
        as a set of name value pairs. While all of the values have string
        representation, validators can be associated with configuration parameters
        to enforce type safeness, and range checking.

A rich set of predefined validators are supplied with the package,
            and custom validators can also be written and used.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Incorporating the socket library | Up | The NSCL Exception class library |
