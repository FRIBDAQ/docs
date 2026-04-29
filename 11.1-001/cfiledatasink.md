|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="daq3_cfiledatasink"></a>CFileDataSink

<a name="AEN23266"></a>## Name

CFileDataSink -- Data sink to a disk file.

<a name="AEN23269"></a>## Synopsis

```
CFileDataSink : public CDataSink
```

<a name="AEN23309"></a>## DESCRIPTION

A `CDataSink` that writes data to a disk file.

<a name="AEN23313"></a>## METHODS



`  CFileDataSink(int fd);`Constructs a file data sink using a file descriptor
                    `fd`.  The
                    file descriptor is something that must have come from
                    functions like `open`,
                    `dup`, `socket` etc.
                    Note that this implies that `CFileDataSink`
                    can actually send data to anything that can be
                    represented by a file descriptor.

If `fd` is not writable (e.g. was opened
                    as O_RDONLY) an
                    `std::string` exception is thrown
                    with text indicating this fact

`  CFileDataSink(std::string path);`Creates a file data sink that sinks to the
                    `path` in the filesystem.
                    `path` must be able to be created
                    and written to once created.  If `path`
                    already exists, all data are overwritten.

If the file could not be opened for write, an
                    `std::string` exceptionis
                    thrown indicating this fact.

` virtual  void  putItem(const  CRingItem&  item);`Puts a ring item (`item`), to file.
                    Any failure is signalled by a `CErrnoException`
                    whose `ReasonCode` reflects the
                    `errno` at the time of the failing function
                    call.

` virtual   void  put(const  void* pData,  size_t nBytes);`Writes `nBytes` of arbitraty data
                    pointed to by `pData` to the file.
                    Errors are signalled via `CErrnoException`
                    exceptions.

`   void  flush();`Ensures that any data buffered by the operating system
                    is actually written to the objet identified by the
                    sink file descriptor.
                    `flush` will block until this has
                    happened.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CDataSink | Up | CRingDataSink |
