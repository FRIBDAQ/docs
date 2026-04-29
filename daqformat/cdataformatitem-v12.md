|  |  |  |
| --- | --- | --- |
| NSCLDAQ Unified Format Library |
| Prev |  | Next |


---

# <a name="AEN7928"></a>CDataFormatItem (v12)

<a name="AEN7932"></a>## Name

CDataFormatItem (v12) -- Document the version of NSCLDAQ format that follows

<a name="AEN7935"></a>## Synopsis

```
#include <v12/CDataFormatItem.h>
namespace v12 {
class CDataFormatItem : public ::CDataFormatItem
{
    // Canonical methods:
public:
    CDataFormatItem();
    
    virtual uint16_t getMajor() const;
    virtual uint16_t getMinor() const;

    virtual std::string typeName() const;
    virtual std::string toString() const;
    
    virtual void* getBodyHeader() const;
    virtual void setBodyHeader(uint64_t timestamp, uint32_t sourceId,
                         uint32_t barrierType = 0);
    
    
};
}                                // v12 namespace

                    
```

<a name="AEN7937"></a>## DESCRIPTION

Data format items are emitted by data generators to document
                    the format of data they are inserting into the event stream.
                    These ring items are relatively minimal, having a header,
                    a uint32_t containing sizeof(uint32_t)
                    and a pair of uint16_t's containing the major and minor
                    versions of the version.

In practice, the minor version is unimportant

<a name="AEN7942"></a>## METHODS



`  CDataFormatItem();`The constructor fills in the item with the
                            major and minor vesions that define the data
                            format.

` const virtual uint16_t  getMajor ();`Returns the major version of the data format.  In
                            practice, this is sufficient to establish the data
                            format.

` const virtual uint16_t  getMinor();`Returns the minor version of the data format.  In practice
                            this is seldom necessary.

` const virtual std::string  typeName();`Return the string:
                            Ring Item format version

` const virtual std::string  toString();`Returns a human readable string that describes the
                            contents of the ring item.

` const virtual void*  getBodyHeader();`Returns nullptr since these items
                            never have a body header.

` virtual void  setBodyHeader(uint64_t  timestamp, uint32_t  sourceId, uint32_t  barrierType  = 0);`No-op since these items don't have body headers.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CAbnormalEndItem (v12) | Up | CGLomParameters (v12) |
