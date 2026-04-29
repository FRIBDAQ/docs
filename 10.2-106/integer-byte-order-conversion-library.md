|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN1391"></a>Chapter 26. Integer byte order conversion library

The cvt package provides functions that convert
        data from foreign host to local host integer formats and back.
        These functions are designed to make use of a byte order signature
        that describes the byte order of the foreign host.

Reference material for this library is available in the
        [[r11080]].

This chapter gives an high level view of how the
        library should be used.

# <a name="AEN1398"></a>26.1. Using the conversion library in your code

The conversion library is a set of C functions.  To use it,
            you will need to include the library header in your source code
            with a line like:

<a name="AEN1401"></a>**Example 26-1. Including the cvt header**

```
#include <cvt.h>
                
```


You will also need to link the conversion library into your executable
            program.  Since the conversion headers and libraries are generally
            not installed in the normal search paths for headers and libraries,
            you will need to help the compiler find them at compile and link time.
            In this discussion, we will assume you have defined an environment
            variable DAQROOT to point to he NSCL DAQ installation directory
            (at the NSCL this will typically be in
            /usr/opt/daq/some-version
            where some-version is the version of the NSCLDAQ
            you are selecting.

<a name="AEN1407"></a>**Example 26-2. Compiling a C or C++ source file that includes cvt.h**

```
gcc -c -I$DAQROOT/include myprogram.c

or

g++ -c -I$DAQROOT/include myprogram.cpp

            
```

<a name="AEN1411"></a>**Example 26-3. A makefile rule that builds a C++ program using the
                cvt package**

```
theprogram: $(OBJECTS)
    g++ -o theprogram $(OBJECTS) -L$(DAQROOT)/lib -lcvt -Wl,"-rpath=$(DAQROOT)/lib"
            
```

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| libraries | Up | Byte order signatures and conversion blocks |
