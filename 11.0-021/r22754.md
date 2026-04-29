|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="daq3_cfiledatasource"></a>CFileDataSource

<a name="AEN22758"></a>## Name

CFileDataSource -- Ring item data source from a file

<a name="AEN22761"></a>## Synopsis

```
  CFileDataSource(URL& url, std::vector<uint16_t> exclusionList);
```

<a name="AEN22777"></a>## DESCRIPTION

Provides a source of ring items from a file.  For information about
            how to directly create and use this object see METHODS
            below.  The normal way to create a data source object, however is to
            use `CDataSourceFactory` to create the correct
            type of data source from a URI

<a name="AEN22782"></a>## METHODS



`  CFileDataSource(URL& url, std::vector<uint16_t> exclusionList);`Creates a file data source.
                        `url` determines which file data
                        will be read from.  The url must have a
                        file: protocol specified.

`exclusionList` is a list of data
                        item types that will not be passed to the caller
                        by `getItem`.

` CRingItem* getItem();`Gets the next ring item from the file whose type is not
                        a type in the constructor's `exclusionList`.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CRingDataSource | Up | CDataSourceFactory" |
