|  |  |  |
| --- | --- | --- |
| NSCLDAQ Unified Format Library |
| Prev |  | Next |


---

# <a name="AEN7855"></a>CAbnormalEndItem (v12)

<a name="AEN7859"></a>## Name

CAbnormalEndItem (v12) -- Encapsulate abnormal end run item.

<a name="AEN7862"></a>## Synopsis

```
#include <CAbnormalEndItem.h>

namespace v12 {
class CAbnormalEndItem : public ::CAbnormalEndItem
{
    CAbnormalEndItem();
    virtual void* getBodyHeader() const;
    virtual void  setBodyHeader(uint64_t timestamp, uint32_t sourceId,
                         uint32_t barrierType = 0);

    virtual std::string typeName() const;
    virtual std::string toString() const;
};

}

                
```

<a name="AEN7864"></a>## DESCRIPTION

Abnormal end runs are sent through the data flow to indicate
                    that a readout failed and that the run must be ended in an
                    incorrect manner.  The item itself only consists of a ring
                    item header (defined in v12/DataFormat.h),
                    and a uint32_t containing sizeof(uint32_t)
                    indicating there is no body header in the item.

<a name="AEN7869"></a>## METHODS



`  CAbnormalEndItem();`Constructs the item.

` const virtual void*  getBodyHeader();`Returns nullptr
                            since these items don't have body headers.

` virtual void   setBodyHeader(uint64_t  timestamp, uint32_t  sourceId, uint32_t  barrierType = 0);`Since the `CAbnormalEndItem`
                            never has a body header, this is a no-op.

` const virtual std::string  typeName();`Returns the string
                            Abnormal End

` const virtual std::string  toString();`Returns the string
                            Abnormal End\n where the
                            \n should be interpreted to mean
                            a new line.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CRingItem (v12) | Up | CDataFormatItem (v12) |
