|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN14587"></a>Chapter 62. Shared memory

The shared memory library, libshm provides
        operating system independent access to shared memory objects.

This library is available for general use, however it's primary
        use is to improve portability of the RingBuffer software within
        the NSCL DAQ system.

To use the software, you must



- Incorporate the library header into your source code
- Link your program to the library run-time


Reference information is available in [[r54420]]

# <a name="AEN14600"></a>62.1. Overview of the API, and using it from within your C++ software

The API is implemented as a C++ class named
            `CDaqSHM` with the following static methods:



- `create` creates a new region.
- `attach` attaches to an existing region.
- `detach` Detaches from a shared memory region.
- `remove` destroys and
                  existing shared memory
- `size` returns the size
                  of a shared memory region in bytes.
- `lastError` retrieves the last error status
- `errorMessage` looks up an error message


Note that the class is not threadsafe in that the error status information
            is static and therefore shared between all threads without any interlocking.

The sample program below creates a new shared memory region (if the
            region does not yet exist), obtains a pointer to it, then some time
            later detaches from it.  The create and attach calls also illustrate
            error management.

<a name="AEN14628"></a>**Example 62-1. Shared memory library example**

```
#include <daqshm.h>                            
#include <string>
...

// Create the shared memory region.. report any error except
// that the region already exists:

bool status = CDAQShm::create("mymemory", 0x10000,    
                            CDAQShm::GroupRead | CDAQShm::GroupWrite |
                            CDAQShm::OtherRead | CDAQShm::OtherWrite);
if (status && (CDAQShm::lastError() != CDAQShm::Exists)) { 
    std::string exception = "Failed to create new shared memory mymemory: ";
    exception += CDAQShm::errorMessage(CDAQShm::lastError());
    throw exception;
}

// Attach to the region:

void* pMemory = CDAQShm::attach("mymemory");     
if (!pMemory) {
    std::string exception = "Failed to attach to shared memory mymemory: ";
    exception            += CDAQShm::errorMesszage(CDAQShm::lastError());
    throw exception;
}

// At this  time pMemory can be used to read/write the shared memory region.

....

if (CDAQShm::detach(pMemory, "mymemory", 0x10000)) {   
    std::string exception = "Failed to detach mymemory: ";
    exception += CDAQShm::errorMessage(CDAQShm::lastError());
}


            
```

[[c14587#shm_includes]]                    Includes the header for the NSCLDAQ shared memory API.
                    See [[x14658]]
                    for information that describes how to ensure this header
                    will be found by the compiler.
                [[c14587#shm_create]]                    Attempts to crate the shared memory. The return value of this
                    method will be
                    true on error.  The first parameter is the
                    name of the shared memory regiuon.  The second its size in bytes.
                    The last an or of masks that describe how users other than
                    the creator can access the region.  The owner will always have
                    read/write access.
                [[c14587#shm_create_fail]]                    If the creation failed for any other reason than the region
                    already existing (CDAQShm::Exists),
                    an exception of type `std::string` is thrown.
                    The contents of the string provide context for the exception
                    as well as the reason the creation failed.
                [[c14587#shm_attach]]                    Attaches to the shared memory region.  The return value a pointer
                    to the shared memory if successful or a null pointer if not.
                    In this example, once more a string exception describing the
                    failure is constructed and thrown if the `attach`
                    failed.
                Once the `attach` has been done,
                    the shared memory can be accessed through the pointer.

[[c14587#shm_detach]]                    Detaches from the memory.  After the
                    `detach`, no gaurantees
                    are made about the pointer returned from the
                    `attach` call and it therefore
                    should not be dereferences
                true is returned on error and
                    once more the example code throws a descriptive string
                    exception.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Parsing and URIs | Up | Compiling/Linking your software with the shared memory API |
