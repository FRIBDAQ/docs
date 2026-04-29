|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN70880"></a>CZMQRingItemThreadedWorker

<a name="AEN70884"></a>## Name

CZMQRingItemThreadedWorker -- ZeroMQ Threaded worker for ZeroMQ

<a name="AEN70887"></a>## Synopsis

```
#include <CZMQRingItemThreadedProcessingElement.h>

class CZMQRingItemThreadedWorker : public CThreadedProcessingElement
{
public:
    CZMQRingItemThreadedWorker(
        const char* routerUri, uint64_t clientId, CSender& sender,
        CProcessor* processor
};
        
```

<a name="AEN70889"></a>## DESCRIPTION

The constructor of this class constructs its base
            class with a `CZMQRingItemWorker`
            as its processor.
            `routerUri` is the ZMQ router
            URI, clientId is the id of the ROUTER client
            (Dealer) this thread represents.
            `sender` is the
            sender to which data are sent and
            `processor` provides the per
            work item processing.

For the expectations of the `processor`
            see `CZMQRingItemWorker`(3daq).

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CThreadedProcessingElement | Up | CZMQRingItemSourceThread |
