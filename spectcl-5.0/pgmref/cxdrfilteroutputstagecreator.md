|  |  |  |
| --- | --- | --- |
| SpecTcl Programming Reference. |
| Prev |  | Next |


---

# <a name="AEN19634"></a>CXdrFilterOutputStageCreator

<a name="AEN19638"></a>## Name

CXdrFilterOutputStageCreator.h -- 
            Create `CXrFilterOutputStage` objects

<a name="AEN19642"></a>## Synopsis

```
#include <CXdrFilterOutputStageCreator.h>


class CXdrFilterOutputStageCreator : public CFilterOutputStageCreator
{
public:

  virtual CFilterOutputStage*  operator()(std::string type);
  virtual std::string document() const;
  virtual CFilterOutputStageCreator* clone();
};


        
```

<a name="AEN19644"></a>## DESCRIPTION

Creates output stages for the XDR filter format.  See
            `CFilterOutputStageCreator` for documentation
            of the methods implemented by this class.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CFilterOutputStageFactory | Up | FilterEventProcessor |
