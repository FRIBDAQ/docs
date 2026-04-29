|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="chapter.exception"></a>Chapter 59. The NSCL Exception class library

C++ provides an error detection/recovery mechanism called
            exception handling.  Exception handling, while not always easy
            to program correctly is well suited to object oriented software
            development.

Exceptions in C++ are objects that are thrown in search of catchers.
            As each call frame is searched for a catcher, and the exception propagates up
            the call chain.  Object destructors for non-dynamically allocated objects
            get called ensuring proper object cleanup.  If an exception can find no
            catcher, the application exits with an error.

The linguistic construction for emitting, or throwing and exception is the
            **throw** statement. For example:

```
throw SomeObject;
            
```


The linguistic mechanism for specifying exception catchers is the
            **try/catch** block:

```
try {
   …
}
catch (SomeType variable) {
   …
}
…
catch (...) {
…
}
            
```


If an exception is thrown within the block body of the **catch**
            statement, the catch blocks are searched for a matching data type, and the
            textually first matching block is executed.  If none match and a
            **catch (...)** is specified it is invoked.

You can also re-throw an exception after processing using an empty **throw**
            statement.  This is used in the following example to destroy some dynamically
            allocated memory.

```
SomeType* pType;
try {
   pType = new SomeType;
   …
}
catch (...) {
    delete pType;
    throw;
}
            
```


Exception catching does allow polymorphism.  For example, suppose we have a base class
            `MyBase` and a derived class `Derived`.

```
try {
    …
    throw Derived;
    …
}
catch (MyBase& reason) {
    …
}
            
```


            The catch block will execute, and if virtual methods are called, the `Derived`
            implementation will be used.
        # <a name="AEN10384"></a>59.1. Incorporating the library in your programs

So much for an introduction to C++ exception handling.  Based on the presentation so far,
                however there are clear advantages to defining a hierarchy of exceptions that derive
                from a common base class that provides a common set of reporting facilities.  The
                NSCL Exception class library in SpecTcl and nscldaq does this.  This library named
                libException.so that can be found in the lib directory of the
                NSCL DAQ or SpecTcl installations.   Linking with that library is a matter of e.g.:

```
g++   …  -L/usr/opt/spectcl/3.2/lib -lException -Wl,"-rpath=/usr/opt/spectcl/3.2/lib"
                
```


Be sure to substitute the correct top level directory for
                /usr/opt/spectcl/3.2 in both places in the example above.

The base class of the library is called `CException`.  All NSCL
                frameworks and applications enclose essentially the entire program or the body of each thread
                in a try/catch block that can catch and report the error information from a
                `CException` prior to exiting.  Your code can catch this or
                derived class issues either for error reporting or error recovery purposes.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| C++ encapsulation of a Tcl API subset | Up | Exception classes |
