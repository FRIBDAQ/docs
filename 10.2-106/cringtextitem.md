|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.cringtextitem"></a>CRingTextItem

<a name="AEN21448"></a>## Name

CRingTextItem -- Encapsulate ring items that are lists of text strings.

<a name="AEN21451"></a>## Synopsis

```
#include <CRingTextItem>
         
```

```
  CRingTextItem(uint16_t type, std::vector<std::string> theStrings);
```

<a name="AEN21545"></a>## Description

Text string items contain lists of null terminated documentation strings.
            These are stored in ring buffers in structures of the type:
            TextItem.  These items have a type code of
            PACKET_TYPES or
            MONITORED_VARIABLES.  These items are used to
            document the set of packets you can expect to see in
            a PHYSICS_EVENT and provide the value of monitored
            process variables respectively.

<a name="AEN21552"></a>## Public member functions

`  CRingTextItem(uint16_t type, std::vector<std::string> theStrings);`Constructs a ring text item of the type specified by
            `type`.  The text strings will be filled in with
            the values of the individual strings in `theStrings`.

The run offset time will be initialized to zero, and the
            absolute timestamp to the construction time of the object.

`  CRingTextItem(uint16_t type, std::vector<std::string> theStrings, uint32_t offsetTime, time_t timestamp);`Constructs a text item in a fully specified way.
            In addition to `type` and `theStrings`
            providing the item type and the strings for the item respectively,
            `offsetTime`, and `timestamp`
            provide the run time offset and absolute timestamp values respectively.

`  CRingTextItem(const CRingItem& rhs)          throws std::bad_cast;`Constructs a text item from a reference to an existing ring item;
            `rhs`.
            If the ring item is not of an appropriate type for a text item,
            a std::bad_cast exception is thrown.

`  CRingTextItem(const CRingTextItem& rhs);`Constructs a functional copy of of an existing text ring item;
            `rhs`.

` CRingTextItem& operator=(const CRingTextItem& rhs);`Provides for assignment between ring text items.  When done, the object
            that is acted on will be a functional copy of the
            `rhs`  object.

` const int operator==(const CRingTextItem& rhs);`Provides for comparison for functional equivalence between two
            ring text items.  The item is compared with
            `rhs`.
            The comparison returns non zero if there is functioal equivalence.

` const int operator!=(const CRingTextItem& rhs);`Returns the logical inverse  of
            `operator==`.

` const std::vector<std::string> getStrings();`Returns the strings in the string list as a vector of strings.

` void setTimeOffset(uint32_t offset);`Sets the time offset at which the item was created to
            `offset`.

` const uint32_t getTimeOffset();`Returns the most recently set time offset for the item.

` void setTimestamp(time_t stamp);`Sets an absolute timestamp for the item.

` const time_t getTimestamp();`Returns the item's absolute timestamp.

<a name="AEN21665"></a>## Exceptions

Construction from a list item can throw a
            std::bad_cast exception if the underlying
            ring item is not either a
            PACKET_TYPES or
            MONITORED_VARIABLES item.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CRingStateChangeItem | Up | CRingPhysicsEventCountItem |
