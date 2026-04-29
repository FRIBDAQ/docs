|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="chapter.cringmaster"></a>Chapter 27. Ring master class library.

The
        RingMaseter
        is a server that manages access to ringbuffers and cleans up ring buffer
        resources left by improperly exiting programs. See
        [[c3544]]
        for more information about that server.

The
        `CRingMaster `
        class is a C++ class that provides access to the ring master in any
        system.  In many cases, this is created, and functions called
        transparently by higher level library modules.

The ring master library is part of the dataflow client library.
        It provides a header
        CRingMaster.h as well.
        The examples below show how to incorporate this header, into your
        source code and compilation, and how to link to the data flow library.
        We assume there's an environment variable named DAQROOT which is the
        top level of the NSCLDAQ installation tree.

<a name="AEN1481"></a>**Example 27-1. Including the header**

```
#include <CRingMaster.h>
        
        
```

<a name="AEN1484"></a>**Example 27-2. Compiling code**

```
g++ -c -I$DAQROOT/include mymodule.cpp
        
```

<a name="AEN1487"></a>**Example 27-3. Linking code to the library**

```
g++ -o myprogram myprogram.cpp -L$DAQROOT/lib -ldataflow -Wl,"-rpath=$DAQROOT/lib"
        
```

[[r11266]]
        provides reference information on this library.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Data conversion | Up | Networked ring buffer access |
