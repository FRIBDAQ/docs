|  |  |  |
| --- | --- | --- |
| NSCLDAQ Unified Format Library |
| Prev | Chapter 1. Introduction | Next |


---

# <a name="AEN20"></a>1.2. Document Organization

The remainder of this document is organized as follows:



- The remainder of this chapter,
                     describes what you need to do to incorporate this library
                     into your program (compilation and link directives).
- [[c49]]
                    Describes the organization of the library.
- [[c171]]
                    Describes the abstract factory design pattern and how it's applied
                    to this library.
- [[c263]]
                    Provides detailed reference pages.

## <a name="AEN35"></a>1.2.1. Incorporating this library into your programs

As with most Linux library installations, there are
                include and lib directories
                under the installation directory.  If $INSTALL_ROOT
                is the top level installation directory, at compilation time you'll
                need to add

<a name="AEN41"></a>```
-I$INSTALL_ROOT/include
                
```

to your compilation flags so that header files can be located
                by the compiler's preprocessor.  Note that there are several
                subdirectories below this top level header directory, however
                you *should not* add those to the header
                file search path.

The software consists of several libraries.  These must
                be added to the link and, since the libraries are shared,
                an rpath directive must be added so that the run time
                loader can locate those libraries when programs using them
                start.

This means adding the following flags to the link command:

<a name="AEN47"></a>```
-L$INSTALL_ROOT/lib -lNSCLDAQFormat \
    -lV10Format -lV11Format -lV12Format -lAbstractFormat \
    -Wl,-rpath=$INSTALL_ROOT/lib
                
```

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Introduction | Up | Library Organization |
