|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.creadoutexception"></a>CReadoutException

<a name="AEN66007"></a>## Name

CReadoutException -- Base class for readout specific exceptions

<a name="AEN66010"></a>## Synopsis

```
#include <CReadoutException>
         
```

```
 class CReadoutException :  public CException {
}
```

<a name="AEN66015"></a>## Description

This class is a place holder in the exception class hierarchy.  It allows
            programmers to catch all readout specific exception by catching exceptions
            of this type.

<a name="AEN66018"></a>## EXAMPLES

<a name="AEN66020"></a>**Example 1. Catching readout specific examples**

```
try {
// Code that might throw one of the readout applications
// exceptions:
...
}
catch (CReadoutException& error) {
    // Process the exception here.
    ...
}
                
```

<a name="AEN66023"></a>## SEE ALSO

[[r65873]]

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CNullTrigger | Up | CScalerBank |
