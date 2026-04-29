|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN55021"></a>CElapsedTime

<a name="AEN55025"></a>## Name

CElapsedTime -- Subsecond measurement of elapsed times.

<a name="AEN55028"></a>## Synopsis

```
#include <CElapsedTime>
class CElapsedTime
{
public:
    CElapsedTime();
    void start();
    double measure() const;

};

        
```

<a name="AEN55030"></a>## DESCRIPTION

This class supports POSIX-.1-2001 conforming sub second interval
            measurement.
            Note that the actual resolution of this timing is dependent on the
            resolution of the underlying system clock used by
            `gettimeofday`(3).

Constructing the object or invoking `start`
            on a constructed object sets a start time.  Subsequent calls to
            `measure` return the elapsed time since
            that start time in double precision seconds.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CRingFileBlockReader | Up | CSocket |
