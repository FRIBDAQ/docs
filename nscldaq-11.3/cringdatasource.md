|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="daq3_cringdatasource"></a>CRingDataSource

<a name="AEN24391"></a>## Name

CRingDataSource -- Ringbuffer data source for ring items.

<a name="AEN24394"></a>## Synopsis

```
#include <CRingDataSource.h>
            
```

```
CRingDataSource
```

<a name="AEN24414"></a>## DESCRIPTION

Concrete `CDataSource` class that implements
            a source of ring items from a live ring.  See the METHODS
            section below for more information about how to create and use
            this data source directly.  Note that a more convenient mechanism
            for generating these data sources is via the
            `CDataSourceFactory` class.

<a name="AEN24420"></a>## METHODS



`  CRingDataSource(URL& url, std::vector<uint16_t> exclusionList, std::vector<uint16_t> sampleList);`Constructs a `CRingDataSource` object.
                        `url` specifies the ring from which
                        data is desired.  This can be a local or remote ring.
                        The url protocol must be a tcp:.

`exclusionList` specifies a
                        list of ring item types that will not be passed to the
                        client via `getItem`

`sampleList` speicfies a list
                        of ring item types that will be sampled from the ring.
                        Item types in this vector may be skipped if the client
                        application falls behind in processing the ring buffer.

` CRingItem* getItem();`Returns the next suitable item from the ring.  This method
                        will block until a suitable item is available.  Suitability
                        is defined by the `exclusionList`
                        and `sampleList` of item types
                        provided whent he data source was constructed taken with
                        the ring backlog.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CDataSource | Up | CFileDataSource |
