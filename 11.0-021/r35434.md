|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="daq3_critical_section"></a>CriticalSection

<a name="AEN35446"></a>## Name

CriticalSection -- Simple, safe critical section

<a name="AEN35449"></a>## Synopsis

```
CriticalSection
```

<a name="AEN35458"></a>## DESCRIPTION

Implements an easy to use critical section on top of a mutex.
        To use, simply construct the CriticalSection object in the block
        that needs synchronization. The constructor will lock the mutex and unlock
        it when destroyed (when the block is exited)

<a name="AEN35461"></a>## EXAMPLE

<a name="AEN35463"></a>```
#include <CMutex.h>
...

CMutex guard;
...
{
    CriticalSection s(guard);                 // Locks guard
    ...
    throw someException;                    // unlocks guard.
    ...
    
}                                           // unlocks guard.

        
```

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CMutex | Up | CCondition |
