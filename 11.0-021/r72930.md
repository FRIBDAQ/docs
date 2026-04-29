|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.cinvalidpacketstateexception"></a>CInvalidPacketStateException

<a name="AEN72934"></a>## Name

CInvalidPacketStateException -- Exception thrown by documented packets.

<a name="AEN72937"></a>## Synopsis

```
#include <CInvalidPacketStateException>
         
```

```
  CInvalidPacketStateException(bool WasOpen, const char* pszAction);
```

<a name="AEN72997"></a>## Description

This exception is thrown when a `CDocumentedPacket`
            is abused.  Specifically if a packet being formatted is begun again,
            or closed one ended.  The best protection against abusing
            `CDocumentedPacket` objects is to
            encapsulate an ordinary `CEventSegment` in
            a `CEventPacket` object as it will
            correctly use the `CDocumentedPacket` to put your
            data inside a packet.

<a name="AEN73005"></a>## Public member functions

`  CInvalidPacketStateException(bool WasOpen, const char* pszAction);`Constructs the exception object.  `WasOpen`
                should be true if the packet was open when this exception was
                thrown.  `pszAction` provides some
                execution context for the exception.

` const int getWasOpen();`Returns non zero if `WasOpen` was true
                when this object was constructed.

` const Int_t ReasonCode();`Returns a code describing the reason for the exception.

` virtual const const char* ReasonText();`Returns a pointer to a string that describes why the
                exception was thrown.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CExperiment | Up | CNullTrigger |
