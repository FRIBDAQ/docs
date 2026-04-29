|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.CErrnoException"></a>CErrnoException

<a name="AEN45786"></a>## Name

CErrnoException -- Exceptions that wrap the Unix `errno`

<a name="AEN45790"></a>## Synopsis

```
CErrnoException
```

<a name="AEN45817"></a>## Description

This exception class wraps the Unix `errno` global variable.
                errno is used by most Unix system calls to provide detailed status
                information.   Constructing this class saves a copy of the `errno`
                variable.   `ReasonCode` will return the saved errno value.
                `ReasonText` will construct a string that includes
                the text associated with the `errno`.

<a name="AEN45826"></a>## Public member functions

`  CErrnoException(const pszAction);``  CErrnoException(const std::string& rsAction);`These constructors save the value of the `errno` variable and
                construct the base class using their parameter as the exception context string
                (returned by `WasDoing`).

` virtual   const const char* ReasonText();`Returns the `sterror` applied to the saved `errno`.

` virtual const Int_t ReasonCode();`Returns the saved `errno` variable value.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CException | Up | CRangeError |
