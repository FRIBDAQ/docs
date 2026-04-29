|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.ceventpacket"></a>CEventPacket

<a name="AEN84687"></a>## Name

CEventPacket -- Encapsulate an event segment in a documented packet.

<a name="AEN84690"></a>## Synopsis

```
#include <CEventPacket>
         
```

```
  CEventPacket(CEventSegment& seg, short tag, std::string name, std::string description, std::string version);
```

<a name="AEN84737"></a>## Description

This class allows you to wrap an existing event segment in a documented
            packet without modification to the event segment.

<a name="AEN84740"></a>## Public member functions

`  CEventPacket(CEventSegment& seg, short tag, std::string name, std::string description, std::string version);`Creates the object.  `seg` is a reference
                to the event segment you want to wrap in a packet.  All the
                remaining parameters define the packet as in
                [[r84400]]

` virtual void initialize();`Invokes the `initialize` method of the
                event segment
                used to construct this object.

` virtual void clear();`Invokes the `clear` method of the
                evnet segment used to create this object.

` virtual void disable();`Invokes the event segment's `disable` method.

` virtual size_t read(void* pBuffer, size_t maxwords);`Begins the packet, invokes the `read`
                method of the encapsulated event segment and ends the
                packet.

<a name="AEN84796"></a>## SEE ALSO

[[r84400]]
[[r84801]]

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CDocumentedPacket | Up | CEventSegment |
