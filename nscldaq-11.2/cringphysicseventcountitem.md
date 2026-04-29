|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.cringphysicseventcountitem"></a>CRingPhysicsEventCountItem

<a name="AEN20034"></a>## Name

CRingPhysicsEventCountItem -- Provides statistics regarding the number of events produced.

<a name="AEN20037"></a>## Synopsis

```
#include <CRingPhysicsEventCountItem.h>
         
```

```
 class CRingPhysicsEventCountItem {
}
```

```
  CRingPhysicsEventCountItem();
```

<a name="AEN20174"></a>## Description

This class encapsulates the
            PhysicsEventCountItem ring item.  That item is used
            to indicate how many events have been acquired so far this run.
            Timestamps and run time offset allow this to be used to compute
            trigger rates.   Clients that need to know the fraction of
            `PHYSICS_EVENT` items they are receiving
            can also use this.

<a name="AEN20179"></a>## Public member functions

`  CRingPhysicsEventCountItem();`Default constructor.  The event count and time offset will be
            zeroed.  The timestamp will be the time the constructor was called.

`  CRingPhysicsEventCountItem(uint64_t count, uint32_t timeOffset);`Constructs an event count item which is initialized with the
            specified `count` of triggers and is
            said to have occured `timeOffset` seconds
            into the run.

`  CRingPhysicsEventCountItem(uint64_t count, uint32_t timeoffset, time_t stamp);`Same as the previous constructor with the added initialization of
            the item's timestamp to `stamp`.

`  CRingPhysicsEventCountItem(uint64_t  timestamp, uint32_t source, uint32_t  barrier, uint64_t  count, uint32_t timeoffset, time_t stamp, int divisor = 1);`Constructs a physics event count item with a full body header.
            The contents of the body header are determined by the values
            of `timestamp`, `source`
            and `barrier`.  The `divisor`
            optional parameter provides support for run time intervals that
            are less than one second.  The actual time in seconds into the
            run is

```
(float)timeoffset/divisor
```

.
        `  CRingPhysicsEventCountItem(const CRingItem& rhs)          throws std::bad_cast;`Constructs an event count item from an existing ring item;
            `rhs`.
            If `rhs` is not of type
            PHYSICS_EVENT_COUNT, a
            `std::bad_cast` exception is thrown.

`  CRingPhysicsEventCountItem(const CRingPhysicsEventCountItem& rhs);`Provides support for copy construction.

` CRingPhysicsEventCountItem& operator=(const CRingPhysicsEventCountItem& rhs);`Provides support for assignment of another event count item,
            `rhs` to the object.

` const int operator==(const CRingPhysicsEventCountItem& rhs);`Provides support for comparing two event count items to each other
            for functional equality.

` const int operator!=(const CRingPhysicsEventCountItem& rhs);`Compares two items for functional equality and returns the logical
            inverse of the result.

` const uint32_t getTimeOffset();`Returns the current value of the time offset field of the item.

` void setTimeOffset(uint32_t offset);`Sets the value of the time offset field of the item to
            `offset`.

` const time_t getTimestamp();`Returns the current timestamp of the item.

` void setTimestamp(time_t stamp);`Sets the object's absolute timestamp to `stamp`.

` const uint64_t getEventCount();`Returns the count of the number of eveents that have been
            accepted in the run so far (according to this item).

` void setEventCount(uint64_t count);`Sets the event count field of the item to `count`.

` virtual  const  std::string typeName();`Returns a text version of the ring item type field. This consists of
            the text Trigger count:.

` virtual const  std::string toString();`Returns a human readable string representation of the item.

<a name="AEN20342"></a>## Exceptions

std::bad_cast is thrown on an attempt to construct
            an event count item out of an item that is not of type
            PHYSICS_EVENT_COUNT.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CPhysicsEventItem | Up | CRingFragmentItem |
