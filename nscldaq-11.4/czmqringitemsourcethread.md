|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN51633"></a>CZMQRingItemSourceThread

<a name="AEN51637"></a>## Name

CZMQRingItemSourceThread -- Provide a thread that routes ring items from a source

<a name="AEN51640"></a>## Synopsis

```
#include <CZMQRingItemSourceThread.h>
class CZMQRingItemSourceThread : public CThreadedProcessingElement
{
public:
    CZMQRingItemSourceThread(const char* ringUri, const char* routerUri);

};

        
```

<a name="AEN51642"></a>## DESCRIPTION

Provides a thread that takes ring items from
            some data source specified by
            `ringUri` and, using the
            ZeroMQ Router/Dealer pattern ROUTER running on
            `routerUri` fans them
            out as work items for parallel processing.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CZMQRingItemThreadedWorker | Up | CCommunicatorFactory |
