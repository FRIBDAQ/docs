|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.CTCLHashTable"></a>CTCLHashTable

<a name="AEN59822"></a>## Name

CTCLHashTable -- 
            Object oriented interface to Tcl's hash table functions.

<a name="AEN59825"></a>## Synopsis

```
#include <TCLHashTable.h>

template <class T>
class CTCLHashTable
{
public:
  CTCLHashTable () ;
  CTCLHashTable (  Tcl_HashTable am_HashTable  );
  CTCLHashTable (const CTCLHashTable& aCTCLHashTable );
  virtual ~CTCLHashTable ( );

  CTCLHashTable operator= (const CTCLHashTable& aCTCLHashTable);

  int operator== (const CTCLHashTable& aCTCLHashTable);

  Tcl_HashTable* getHashTable() const;

  void Enter (const std::string& rKey, rCTCLTHashTableItem rValue);
  const CTCLTHashTableItem* Find (const std::string& rsKeyword) const;
  CTCLTHashTableItem* Delete (const std::string& rsKeyword);
  CTCLTHashTableIterator begin ();
  CTCLTHashTableIterator end ();
  std::string Statistics ();
};

    
```

<a name="AEN59827"></a>## DESCRIPTION

Hash tables are tables of keyword value pairs that are organized
            such that the lookup time for any key in the table is *amortized
            constant*.  Hash tables operate by running the key through a
            function called the *hash function*, and storing the
            key/value pair as an element of an array indexed by the result of that hash
            function (*hash index*).  Depending on the implementation of the hash table, different
            methods are used to resolve cases where two keys result in the same
            hash index.

Tcl includes support libraries for hash tables with string keys and
            arbitrary value types (e.g. structures, pointers etc. etc.).  One example
            of the use of this sort of data structure is Tcl's storage of array variables.
            Each array is a hash table indexed by the hash index of the array subscripts.
            In this way Tcl supports subscripts that are arbitrary strings without
            any search overhead when referencing an element of the array.

The `CTCLHashTable` and related classes provide an object oriented
            interface to the Tcl API for hash tables.  This class is a *template class*.
            The template parameter is the type of data that will be associated with each
            hash key.  For example, to create a has key of `CSpectrum*`
            (pointers to SpecTcl Spectra):

```
        CTCLHashTable<CSpectrum*> spectrumHashTable;
            
```

<a name="AEN59839"></a>## METHODS



```
CTCLHashTable
```


Three methods for creating `CTCLHashTable` objects
            are defined.   The first of these creates a new, empty hash table.
            The second, takes the handle to an existing hash table;
            Tcl_HashTable `aHashTable` and wraps
            a `CTCLHashTable` around this existing hash table
            providing an object oriented interface to that hash table.
            The final constructor, a copy constructor, creates a
            `CTCLHashTable` that refers to the same underlying
            Tcl_HashTable as the `aCTCLHashTable` parameter.



```
operator
```


`operator=`  assigns `rhs` to an existing
            object.  The semantics of assignment are that
            followingt assignment, `*this` and `rhs`
            will refer to the same underlying hash table.

`operator==` compares two hash tables, `*this`
            and `rhs` for equality.  The semantics of equality are
            that the two `CTCLHashTable` objects refer to the same
            underlying Tcl hash tables.



```
getHashTable
```


Gets the underlying Tcl_HashTable that is wrapped by
            a `CTCLHashTable` object.



```
Enter
```


Adds an entry to a hash table.  `rKey` is the
            lookup key that will be associated with the entry.  `rValue`
            is the data that is associated with that key.  Note that T
            is the template type that was used to create the hashtable.  E.g. if the
            hash table is a `CTCLHashTable<float>`,
            `rValue` must be a `CTCLHashTableItem<float>`.
            Note that Tcl hash tables do not support duplicate keys.  If a hash table
            entry with the key `rKey` already is in the table it is
            replaced.



```
Find
```


Looks up a hash table item by key.  If a hash table item with
                the key `rsKeyword` exists, a pointer to its
                entry is returned.   If `rsKeyword` has not
                yet been `Enter`ed in the hash table, a
                NULL pointer is returned.



```
Delete
```


Removes the hash table entry with the key `rsKeyword`.
                If the item existed, a pointer to it is returned.  If the item does not
                exist in the hash table a NULL pointer is returned.



```
begin
```


`begin` returns an *iterator* that
                "points" to the first entry in the hash table.  dereferencing the
                iterator yields the pointer to a HashTableItem.  The iterator can be
                incremented via ++ so that it advances to the next item in the table.

`end`returns an iterator that points past the end of the
                table and can be used to determine when iteration is complete.

Iterators are pointer like objects.  See the STL reference below for more
                information about them.  The following example Takes a Hash table and
                counts up the number of elements it contains.

```
        CTCLHashTableIterator i = table.begin();    // Table a CTCLHashTable
        int                   n = 0;
        while (i != table.end()) {
            n++;
        }
        // N is a count of elements in the table.

            
```




```
Statistics
```


Returns a string that contains statistics about the hash table.
            This is a wrapper for `Tcl_HashStats`

<a name="AEN59940"></a>## SEE ALSO

CTCLHashTableItem(3),
CTCLHashTableIterator(3),
Tcl_HashStats(3tcl)

<a name="AEN59943"></a>## REFERENCES



```
Algorithms + Data Structures = Programs
```

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CTCLFileHandler | Up | CTCLHashTableItem |
