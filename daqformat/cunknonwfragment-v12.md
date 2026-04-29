|  |  |  |
| --- | --- | --- |
| NSCLDAQ Unified Format Library |
| Prev |  | Next |


---

# <a name="AEN9301"></a>CUnknonwFragment (v12)

<a name="AEN9305"></a>## Name

CUnknownFragment (v12) -- Fragment item that does not contain a ring item.

<a name="AEN9308"></a>## Synopsis

```
#include <v12/CUnknownFragment.h>

namespace v12 {

class CUnknownFragment : public ::v12::CRingFragmentItem
{
    // Canonical methods:
    
public:
    CUnknownFragment(uint64_t timestamp, uint32_t sourceid, uint32_t barrier,
                     uint32_t size, const void* pPayload);
    virtual ~CUnknownFragment();
public:

    std::string typeName() const;
    
};

}
                        
```

<a name="AEN9310"></a>## DESCRIPTION

This class is just a `v12::CRingFragmentItem`
                        with a payload that is not a ring item. As such

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CRingTextItem (V12) | Up | Sample Program(s) |
