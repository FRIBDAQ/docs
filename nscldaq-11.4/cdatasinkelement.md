|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN51448"></a>CDataSinkElement

<a name="AEN51452"></a>## Name

CDataSinkElement -- Forward data to some sink.

<a name="AEN51455"></a>## Synopsis

```
#include <CDataSinkElement.h>

class CDataSinkElement : public CProcessingElement
{
public:
    CDataSinkElement(CReceiver& src, CSender& sink);
    
    virtual void operator()();
    virtual void process(void* pData, size_t nBytes);

};
        
```

<a name="AEN51457"></a>## DESCRIPTION

This class is intended to be used at the end
            of the processing pipeline.  It simply accepts
            work items and sends them to a sink.  A usual
            application transforms a set of input work items
            into an output set via a parallel application.

While the last stage of that computation could output
            those data, it would then be more work to
            insert additional processing layers in the application
            as it's incrementally built and tested.
            Having a dedicated processing element to output
            data allows for that code to live on its own
            where additional processing stages could be inserted
            prior to it.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CZMQDealerTransport | Up | CDataSourceElement |
