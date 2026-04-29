|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN69375"></a>CThreadedProcessingElement

<a name="AEN69379"></a>## Name

CThreadedProcessingElement -- Run a processing element ina thread.

<a name="AEN69382"></a>## Synopsis

```
#include <CThreadedProcessingElement.h>

class CThreadedProcessingElement : public Thread
{
public:
    CThreadedProcessingElement(CProcessingElement* processor);
    
    virtual void run();
};

        
```

<a name="AEN69384"></a>## DESCRIPTION

In shared memory multiprocessing parallelism,
            it's often simplest to run each parallel processing
            element in a thread of its own.  Each thread then
            gets scheduled to available cores in the system
            by the underlying scheduler.  This class
            leverages the `Thread`(3daq)
            class in NSCLDAQ to embed a
            `CProcessingElement` in a thread
            of execution.

When the application initialization code runs a threaded
            parallel program, it sets up all the transports,
            senders and reveivers, creates the processors and
            then constructs a `CThreadedProcessingElement`
            for each processor.  Processors are then started
            using the `Thread` class's
            `start` method. 
            When the thread begins execution it will call
            the `operator()` method of the
            `processor` it was constructed
            with.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CRingItemSorter | Up | CZMQRingItemThreadedWorker |
