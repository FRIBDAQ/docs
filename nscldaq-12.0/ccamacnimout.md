|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="CCamacNimout"></a>CCamacNimout

<a name="AEN43454"></a>## Name

CCamacNimout -- Provides low level support for the BiRa CAMAC Nim output module.

<a name="AEN43457"></a>## Synopsis

```
#include <CCamacNimout.h>
            
```

```
  CCamacNimout(unsigned int b, unsigned int c, unsigned int n);
```

<a name="AEN43485"></a>## Description

Provides low level object oriented support for the BiRa CAMAC Model 3251 NIM output
                register.  Creating an intance of this class allows you to manipulate a physical
                module.

<a name="AEN43488"></a>## Public member functions



<a name="AEN43493"></a>`                    CCamacNimout(unsigned int b, unsigned int c, unsigned int n);`

Constructs a `CCamacNimout` object to control the
                            module defined at `b, c, ` and `n`

<a name="AEN43513"></a>` void >WriteMask(unsigned short mask);`

Writes the specified
                            `mask` of bits to the output register.
                            What this actually does will depend on the jumpers in the modules.
                            If the jumpers are pulse mode (normal at the NSCL), all the ones bits in the
                            mask will get pulsed as nim trues for some time that is
                            defined by the module hardware.

<a name="AEN43526"></a>` void WriteBit(unsigned int nBitno);`

Writes a mask that consists only of the specific bit `nBitno`.
                            This is the same as calling `WriteMask` with the value
                             1 << nBitno  as the parameter.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CCamacModule | Up | CCrateController |
