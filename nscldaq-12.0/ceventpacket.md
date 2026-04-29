|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.ceventpacket"></a>CEventPacket

<a name="AEN103901"></a>## Name

CEventPacket -- Encapsulate an event segment in a documented packet.

<a name="AEN103904"></a>## Synopsis

```
#include <CEventPacket>
         
```

```
  CEventPacket(CEventSegment& seg, short tag, std::string name, std::string description, std::string version);
```

<a name="AEN103951"></a>## Description

This class allows you to wrap an existing event segment in a documented
            packet without modification to the event segment.

<a name="AEN103954"></a>## Public member functions

`  CEventPacket(CEventSegment& seg, short tag, std::string name, std::string description, std::string version);`Creates the object.  `seg` is a reference
                to the event segment you want to wrap in a packet.  All the
                remaining parameters define the packet as in
                [[r103614]]

` virtual void initialize();`Invokes the `initialize` method of the
                event segment
                used to construct this object.

` virtual void clear();`Invokes the `clear` method of the
                evnet segment used to create this object.

` virtual void disable();`Invokes the event segment's `disable` method.

` virtual size_t read(void* pBuffer, size_t maxwords);`Begins the packet, invokes the `read`
                method of the encapsulated event segment and ends the
                packet.

<a name="AEN104010"></a>## SEE ALSO

[[r103614]]
[[r104015]]

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CDocumentedPacket | Up | CEventSegment |
