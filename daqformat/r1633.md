|  |  |  |
| --- | --- | --- |
| NSCLDAQ Unified Format Library |
| Prev |  | Next |


---

# <a name="AEN1633"></a>CRingFragmentItem (abstract)

<a name="AEN1637"></a>## Name

CRingFragmentItem (abstract) -- Ring item to encapsulate event builder fragments.

<a name="AEN1640"></a>## Synopsis

```
#include <CRingFragmentItem.h>

class CRingFragmentItem : public CRingItem
{
 

public:
  CRingFragmentItem(uint64_t timestamp, 
		    uint32_t source, 
		    uint32_t payloadSize, 
		    const void* pBody,
		    uint32_t barrier=0);

  virtual uint64_t     timestamp() const;
  virtual uint32_t     source() const;
  virtual size_t       payloadSize() const;
  virtual void*        payloadPointer();
  virtual uint32_t     barrierType() const;

  virtual std::string typeName() const;
  virtual std::string toString() const;
  
  virtual void setBodyHeader(uint64_t timestamp, uint32_t sourceId,
                         uint32_t barrierType = 0) ;
  
  virtual void* getBodyHeader() const;
  virtual bool hasBodyHeader() const;


};
                
```

<a name="AEN1642"></a>## DESCRIPTION

The event builder sort stage can output a set of fragments
                    encapsulated in a ring item. The fragments look like
                    a ringitem header, a body header and an arbitrary payload.
                    The `CRingFragmentItem` represents
                    the items where the payload are established to be ring items
                    (note that the sort stage of the event builder is format
                    agnositic).

<a name="AEN1646"></a>## METHODS



`  CRingFragmentItem(uint64_t  timestamp, uint32_t  source, uint32_t  payloadSize, const void*  pBody, uint32_t  barrier = 0);`Constructs the item.  The `timestamp`,
                            `sourcde` and optional
                            `barrier` parameters fill in
                            the body header.  The default value of 0
                            for the `barrier` represents a
                            non-barrier event.

The payload of the fragment is `payloadSize`
                            bytes taken from the data pointed to by `pBody`.

For this item, type, `pBody`
                            is expected to point to a ring item whose
                            header size field is the same as the
                            `payloadSize` parameter.

` const virtual uint64_t      timestamp();`Returns the timestamp from the item's body header.
                            Note that by definition, fragment items have
                            a body header.

`  const virtual uint32_t      source();`Returns the source id from the item's body header.

` const virtual size_t   payloadSize();`Returns the size of the payload. Note that it is
                            acceptable, and normal for this to be computed by the
                            implementation from the ring item size and the body
                            header size

` virtual void*         payloadPointer();`Returns a pointer to the payload data.  The pointer
                            allows the data to be edited as well as simply
                            inspected.

` virtual uint32_t      barrierType();`Returns the item's body header barrier type field.

` const virtual std::string  typeName();`Returns a string that describes the type of the
                            ring item: Event fragment

` const virtual std::string  toString();`Returns a string representation of the  contents of
                            the ring item. This is used e.g. by
                            **dumper**

` virtual void  setBodyHeader(uint64_t  timestamp, uint32_t  sourceId, uint32_t  barrierType  = 0);`Modifies the contents of the item's body header
                            (this type always has  a body header).

` const virtual void*  getBodyHeader();`Returns a pointer to the object's body header.
                            Note that the actual shape of the body header
                            depends on the actual data format version.  Normally
                            each data version has an associated
                            DataFormat.h header which, among other
                            things defines a BodyHeader type
                            within a namespace specific to the format.

` const virtual bool  hasBodyHeader();`Returns true as this type of ring item
                            always has a body header.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CPhysicsEventItem (abstract) | Up | CRingPhysicsEventCountItem (abstract) |
