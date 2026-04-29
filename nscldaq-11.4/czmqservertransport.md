|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN51278"></a>CZMQServerTransport

<a name="AEN51282"></a>## Name

CZMQServerTransport -- ZeroMQ transport that does a listen.

<a name="AEN51285"></a>## Synopsis

```
#include <CZMQServerTransport.h>

class CZMQServerTransport : public CZMQTransport
{
public:
    CZMQServerTransport(const char* pUri, int socketType);
};

        
```

<a name="AEN51287"></a>## DESCRIPTION

This clss is a ZeroMQ transport for a socket
            that listens for connections rather than invoking
            `connect`.
            `pUri` is a URi that specifies the
            socket endpoint and `socketType`
            is the ZeroMQ socket type e.g. ZMQ_PUB.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CZMQClientTransport | Up | CZMQRouterTransport |
