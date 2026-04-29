|  |  |  |
| --- | --- | --- |
| Batch SpecTcl (5.2 and later) |
| Prev |  | Next |


---

# <a name="AEN690"></a>CDataGetter

<a name="AEN694"></a>## Name

CDataGetter -- Base class for data getters.

<a name="AEN697"></a>## Synopsis

```
#include <CDataGetter.h>

class CDataGetter
{
public:
    virtual ~CDataGetter() {}               
    virtual std::pair<size_t, void*> read() = 0;  
    virtual void free(std::pair<size_t, void*>& data) =0; 
};

                    
```

<a name="AEN699"></a>## DESCRIPTION

This class is documented in case you want to add additional
                        data sources to batch SpecTcl.  The `CDataGetter`
                        class is the base class for such objects.  Concrete
                        subclasses must implement two methods;
                        `read` and `free`.



` virtual  std::pair<size_t, void*>  read();`This is expected to read another chunk of data
                                    from the data source.  The return value is
                                    a pair that provides the amount of data
                                    read (in bytes) and a pointer to that data.
                                    The data may be dynamically or statically
                                    allocated.  The current version of the
                                    SpecTcl Batch analyzer will only have one
                                    block of data *active* at
                                    a time, that is `free`
                                    will be called prior to the next invocation
                                    of `read`

` virtual   void  free(std::pair<size_t, void*>&  data);`Called when the analyzer is done with a block
                                    of data.  If the data was dynamically allocated,
                                    this method should free it.  The
                                    parameter is a reference to the result of
                                    the most recent call to `read`.
                                    Only one block of data will be in analysis
                                    in this SpecTcl at a time.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| filesource | Up | CDataDistributor |
