|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="CCAMACScalerLRS2551"></a>CCAMACScalerLRS2551

<a name="AEN30350"></a>## Name

CCAMACScalerLRS2551 -- Support software for the LeCroy LRS 2551 12 channel CAMAC scaler

<a name="AEN30353"></a>## Synopsis

```
#include <CCAMACScalerLRS2551.h>
            
```

```
  CCAMACScalerLRS2551(unsigned int b, unsigned int c, unsigned int n);
```

<a name="AEN30386"></a>## Description

This class is intended to provide high level support for the LeCroy LRS 2551
                12 channel camac scaler module.  The module works best within the
                production readout framework, as the `CScaler` base class
                matches the needs and interface requirements of registered scalers.

<a name="AEN30390"></a>## Public member functions



<a name="AEN30395"></a>`  CCAMACScalerLRS2551(unsigned int b, unsigned int c, unsigned int n);`

Creates a new `CCAMACScalerLRS2551` object
                            that can be used to manipulate an actual scaler modulea the
                            CAMAC address described by the `b, c` and
                            `n` function arguments.

<a name="AEN30415"></a>`virtual void  Initialize(void);`

Prepares the module for data taking; the module scaler channels are cleared.

<a name="AEN30425"></a>`void   Read (std::vector<unsigned long>%amp; Scaleres);`

Reads all 12 channels of scaler from the module and appends them to the
                            `Scaler` vector.

<a name="AEN30438"></a>`void   Clear (void);`

Clears all channels of the scaler.

<a name="AEN30448"></a>`  (void);`

Returns 12, the number of scaler channels the module will add
                            to to the output buffer when it is read.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CCAENV977 | Up | CCAMACScalerLRS4434 |
