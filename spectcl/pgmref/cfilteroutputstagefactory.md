|  |  |  |
| --- | --- | --- |
| SpecTcl Programming Reference. |
| Prev |  | Next |


---

# <a name="AEN19862"></a>CFilterOutputStageFactory

<a name="AEN19866"></a>## Name

CFilterOutputStageFactory -- Create filter output stage objects.

<a name="AEN19869"></a>## Synopsis

```
#include <CFilterOutputStageFactory.h>

class CFilterOutputStageFactory {
public:
  static CFilterOutputStageFactory& getInstance();
  
  CFilterOutputStage* create(std::string type) const;
  void                Register(CFilterOutputStageCreator& creator);
  std::string         document() const;

};

        
```

<a name="AEN19871"></a>## DESCRIPTION

The `CFilterOutputStageFactory`  singleton
            is used to create filter filter output stages to associate with
            filters once their `-format` is known.

The filter output stage is then responsible for actually writing
            filtered events to the output file.

<a name="AEN19877"></a>## METHODS



` static   CFilterOutputStageFactory&  getInstance();`Returns a pointer to the singleton instance of this
                        class.   Note that if necessary the object is constructed.
                        Constructors for this class are private
                        to enforce the singleton nature of this object.

`  const CFilterOutputStage*  create(std::string  type);`Iterates over the registered filter output stage creators
                        asking them to create a new output stage for the
                        format specified by `type`.

`   void Register(CFilterOutputStageCreator&  creator);`Provides a new output stage creator to the factory.
                        Output stage creators are the objects that actually
                        create filter output stages.

See `CFilterOutputStagereator`
                        for information about filter output stage creators

`  const  std::string  document();`Collects all of the documentation strings from
                        the registered creators separated by newlines.
                        This is used by the **filter** command
                        to generate help text that describes the available
                        output formats.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CFilterOutputStageCreator | Up | CXdrFilterOutputStageCreator |
