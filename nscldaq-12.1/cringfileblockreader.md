|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN54984"></a>CRingFileBlockReader

<a name="AEN54988"></a>## Name

CRingFileBlockReader -- CRingBlockreader that reads from file.

<a name="AEN54991"></a>## Synopsis

```
#include <CRingFileBlockReader.h>
class CRingFileBlockReader : public CRingBlockReader
{
public:
  CRingFileBlockReader(const char* filename);
  CRingFileBlockReader(int fd);
 
};


        
```

<a name="AEN54993"></a>## DESCRIPTION

This is a concrete subclass of `CRingBlockReader`
            that reads data from a file.

<a name="AEN54997"></a>## METHODS



`  CRingFileBlockReader(const  char*  filename);`Constructs the object using `filename`
                        a path to the file to be opened.  The file  must
                        be readable by the effective user id of the
                        runnning process.

`   CRingFileBlockReader(int int fd);`Constructs the reader on a file alread opened on the
                        file descriptor `fd`

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CRingBlockReader | Up | CElapsedTime |
