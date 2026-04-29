|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN70528"></a>CZMQClientTransport

<a name="AEN70532"></a>## Name

CZMQClientTransport -- ZeroMQ transport that does a connect.

<a name="AEN70535"></a>## Synopsis

```
#include <CZMQClientTransport>

class CZMQClientTransport : public CZMQTransport
{
public:
    CZMQClientTransport(const char* pUri, int socketType);
};
        
```

<a name="AEN70537"></a>## DESCRIPTION

represents a ZeroMQ transport that performs a
            `connect` operation to
            obtain a peer socket.
            `pUri` is a ZeroMQ compatible
            URI that specifies the endpoint and
            `socketType` is the
            ZeroMQ socket type (e.g. ZMQ_PULL).

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CZMQTransport | Up | CZMQServerTransport |
