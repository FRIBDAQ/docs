|  |  |  |
| --- | --- | --- |
| NSCLDAQ Unified Format Library |
| Prev |  | Next |


---

# <a name="AEN5748"></a>CPhysicsEventItem (v11)

<a name="AEN5752"></a>## Name

CPhysicsEventItem (v11) -- Encapsulate a physics event.

<a name="AEN5755"></a>## Synopsis

```
#include <v11/CPhysicsEventItem>


namespace v11 {

class CPhysicsEventItem : public ::CPhysicsEventItem
{
public:
  CPhysicsEventItem(size_t maxBody=8192);
  CPhysicsEventItem(                                 // Our factory can use this.
       uint64_t timestamp, uint32_t source, uint32_t barrier,
       size_t maxBody=8192
   );
  virtual size_t getBodySize()    const;
  virtual const void*  getBodyPointer() const;
  virtual void* getBodyPointer();
  virtual bool hasBodyHeader() const;
  virtual uint64_t getEventTimestamp() const;
  virtual uint32_t getSourceId() const;
  virtual uint32_t getBarrierType() const;

  virtual std::string typeName() const;	// Textual type of item.
  virtual std::string toString() const; // Provide string dump of the item.

  virtual void* getBodyHeader() const;
  virtual void setBodyHeader(
        uint64_t timestamp, uint32_t sourceId,
        uint32_t barrierType = 0
  );

 
 
};
}

                
```

<a name="AEN5757"></a>## DESCRIPTION

Ring item to encapsulate the application
                    specific physics event data ring item.

<a name="AEN5760"></a>## METHODS



`  CPhysicsEventItem(size_t  maxBody = 8192);`Constructs an item for a single physics trigger.
                            Note that the storage size is statically allocated
                            with `maxBody` bytes of payload
                            data.  The ring item header type field is initialized
                            to PHYSICS_EVENT.

Upon creating the item, if a body header
                            is required, `setBodyHeader`
                            is invoked.  `getBodyCursor`
                            is then used get a pointer into the object at where
                            the physics data should be put.  After incrementing
                            this pointer by an appopriate amount,
                            calls to `setBodyCursor`,
                            folowed by `updateSize`
                            are required to set the size field of the
                            ring item header.

` const virtual std::string  typeName();`Returns a string that represents the ring item type:
                            Event

` const virtual std::string  toString();`Returns a string that represents the contents of the
                            event.  This is used, e.g., by the
                            **dumper** command to render human
                            readable data.

` const virtual void* getBodyHeader();`Returns a pointer to the body header for the event.
                            If the event has no body header,
                            nullptr is returned. Note that
                            the base class `hasBodyHeader`
                            can be called to determine if the ring item type has
                            a body header.

` virtual void  setBodyHeader(uint64_t  timestamp,  uint32_t  sourceId, uint32_t  barrierType  = 0);`Inserts a new or modifies an existing body header of the event.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CGlomParameters (V11) | Up | CRingFragmentItem (v11) |
