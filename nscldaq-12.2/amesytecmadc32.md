|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN105086"></a>AMesytecMADC32

<a name="AEN105090"></a>## Name

AMesytecMADC32 -- Support for REA3 diganostics use of Mesytec MADC32

<a name="AEN105093"></a>## Synopsis

```
package require AMesytecMADC32
AMesytecMADC32 create dev-name

addtcldriver create stack-name  -ensemble dev-name
        
```

<a name="AEN105098"></a>## DESCRIPTION

Provides hard coded support for the Meystec MADC32 as a Tcl module.  I believe this
            was written for the REA3 diagnostic system by Scott Williams though there is no
            attribution nor purpose in the code.   The **madc** command provides
            more general support and is recommended for current use.

Initialization sets the module into single event mode and sets all threshold
            values to zero.  This results in non zero-suppressed data.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| ALevel3XLM72 | Up | APpacXLM72 |
