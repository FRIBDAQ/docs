|  |  |  |
| --- | --- | --- |
| NSCLDAQ Unified Format Library |
| Prev |  | Next |


---

# <a name="AEN974"></a>CRingItem (abstract)

<a name="AEN978"></a>## Name

CRingItem -- Ultimate ring item base class

<a name="AEN981"></a>## Synopsis

```
#include <CRingItem.h<

class CRingItem {

public:
      CRingItem(uint16_t type, size_t maxBody = CRingItemStaticBufferSize - 10);

      CRingItem(const CRingItem& rhs);
      CRingItem(pRingItem pItem);
      virtual ~CRingItem();
      virtual size_t getStorageSize() const;
      virtual size_t getBodySize()    const;
      virtual const void*  getBodyPointer() const;
      virtual void* getBodyPointer();
      void*  getBodyCursor();
      pRingItem  getItemPointer();
      const RingItem*  getItemPointer() const;
      uint32_t type() const;
      uint32_t size() const;
      virtual bool mustSwap() const;
      virtual bool hasBodyHeader() const;
      virtual void* getBodyHeader() const = 0;
      virtual uint64_t getEventTimestamp() const;
      virtual uint32_t getSourceId() const;
      virtual uint32_t getBarrierType() const;
      virtual void setBodyHeader(uint64_t timestamp, uint32_t sourceId,
                         uint32_t barrierType = 0) = 0;
      virtual void setBodyCursor(void* pNewCursor);
      virtual void updateSize();          
      virtual std::string typeName() const; 
      virtual std::string toString() const; 
      virtual void* appendBodyData(const void* pSrc, uint32_t nBytes);


};
                
```

<a name="AEN983"></a>## DESCRIPTION

This is the ultimate base class for all ring item format classes.
                    It lives in the global namespace.  It provides interfaces
                    and services used by other derived classes.

While most of the virtual methods have default implementations,
                    if you are building a new formatting class hierarchy, you should
                    not count on those doing what you want if they require
                    knowledge of the format of the ring item format.

<a name="AEN987"></a>## METHODS



`  CRingItem(uint16_t type, size_t  maxBody = CRingItemStaticBufferSize - 10);`Constructor.  `type` will be stored
                            in the ring item header's type field.  Note that
                            the header form is common for all formats.
                            The `type` is 16 bit wide because in
                            the original design it was also used to determine the
                            byte order of the originator.  Specifically, if the
                            'low order' 16 bits of a type field were zero, the
                            byte order of the originator was the opposite of the
                            consumer.  Now that little-endianess has won the
                            byte order wars and big-endinaness only appears
                            vestigially in network byte ordering,  We define
                            the byte ordering of Ring items to be little-endian.

`maxBody` determines the maximum
                            number of bytes the internal storage for the ring item
                            can hold in the body (the part following the header).
                            Note that the design of `CRingItem`
                            includes a decently sized static block of data.
                            If this value indicates the data will fit in that
                            block, no dynamic memory allocation is required and
                            that block is used.  If this value indicates that
                            the data won't fit, a block is dynamically allocated
                            and used.  The intent is to minimize the costly
                            set of dynamic memory allocations/deallocations
                            needed if all `CRingItem`
                            constructions dynamically allocated the needed
                            data.

The default value for `maxBody`
                            allows callers to use the static buffer and is
                            defined in CRingItem.h.

`  CRingItem(pRingItem  pItem);`Wraps a `CRingItem` object
                            around a raw ring item.  The type
                            pRingItem is defined in
                            DataFormat.h.

`pItem` is used to size
                            the ring item and copied into the data storage
                            region of the item.  The body cursor is set to point
                            after the ring item data.  This allows the
                            item to be mutated (via `getBodyPointer`)
                            and to be extended (via `getBodyCursor`,
                            `setBodyCursor`, and `updateSize`).

` const virtual size_t  getStorageSize();`Returns the capacity of the block of data that is being used
                            to store the ring item.   Can be used to determine
                            if sufficient storage has been allocated to
                            hold the desired ring item.

` const virtual size_t  getBodySize();`Returns the current size, in bytes,
                            of the ring item body.
                            This computes the number of bytes between the
                            pointers returned by
                            `getBodyCursor` and the
                            `geBodyPointer`.  For it to be
                            accurate, `getBodyCursor`
                            must be updated (via `setBodyCursor`)
                            to point past the body of the ring item as it is
                            so far.

` const virtual const void*   getBodyPointer();`Returns a pointer to the body of the item. Since
                            the pointer is const, this is intended to allow
                            read access.  Note that the concept of a ring item
                            *body* is not that straightforward.
                            In version 10, for example the body begins right after
                            the ring item header.  In v11, v12, which support body
                            headers the body may begin after the uint32_t
                            indicating there is no body header (which has different values
                            depending on version) or it may begin after the body
                            header if there is on.  Therefore, this is virtual
                            and implemented on a per version basis.

`  virtual void*  getBodyPointer();`Same as above except that the pointer can be used
                            to modify the body contents.

` void*   getBodyCursor();`Returns the body cursor of the item. When a ring item
                            is created, a pointer, called the body cursor is
                            created which points to the first free byte of memory
                            into which data can be appended to the ring item.
                            As data are appended to the ring item, the
                            object's body cursor should be reste with
                            `setBodyCursor`, at some point,
                            when the ring item has been completely built,
                            `updateSize` should be called
                            to compute the ring item's size and store it in the
                            size field of the ring item's header.

` pRingItem   getItemPointer();`Returns a pointer to the ring item as encapsulated
                            by this class.  Note that pRingItem
                            is defined in DataFormat.h.

` const const RingItem*   getItemPointer();`Same as above but the pointer only allows read access
                            to the contents of the ring item.

` const uint32_t  type();`Returns the full 32 bit type field of the
                            ring item.

` const uint32_t  size();`Returns the size field of the header. Note that unless
                            `updateSize` has been called,
                            this value is not a reliable measure of the number
                            of bytes that make up the ring item.

`  const virtual bool  mustSwap();`Returns false.  All data is
                            now specified be little endian as are all computing
                            systems processing that data.

` const virtual bool  hasBodyHeader();`Returns true if the ring item
                            has a body header.

` const virtual void*  getBodyHeader();`Returns a pointer to the body header of the item
                            if it has one.  If it does not returns a
                            nullptr.

` const virtual uint64_t  getEventTimestamp();`Returns the event/fragment timestamp stored
                            in the body header of the ring item.  If the ring
                            item has no body header,
                            `std::logic_error` is thrown.
                            You can use e.g. `hasBodyHeader`
                            to test for the presence of a body header in the
                            item.

` const virtual uint32_t  getSourceId();`Retrieves the source id from the ring item's body header.
                            If the ring item does not have a body header,
                            `std::logic_error` is throw

` const virtual uint32_t  getBarrierType();`Returns the barrier type field from the item's
                            body header.   If the ring item does not have a body
                            header, `std::logic_error`
                            is thrown.

(pure virtual)
                        ` virtual void  setBodyHeader(uint64_t  timestamp, uint32_t  sourceId, uint32_t  barrierType = 0);`If the format supports body headers a body header is
                            added to the item (if it does not already have one) or
                            the body header is modified as described by the method's
                            parameters.  If the format does not support body headers,
                            this should be implemented as a no-op.

Note that body data must never be overwritten.
                            If an item has a non-empty body but no body header,
                            then that body must be moved to make space for the
                            body header which is then put in the appropriate
                            place (after the ring item header in currently
                            supported formats).

` virtual void  setBodyCursor(void*  pNewCursor);`Updates the internal body cursor of the object
                            with `pNewCursor`.  If coupled
                            with a call to `updateSize`,
                            this causes the size field of the ring item header
                            to be computed and updated.

` virtual void updateSize();`Treating the current body cursor value as a pointer
                            to the byte following the current contents of the
                            ring item, the size of the ring item is computed
                            and stored in the size field of the ring item
                            header.

` () const virtual std::string  typeName();`The base class returns the string:
                            Unknown followed by the parenthesized
                            numeric
                            type from the ring item header in hexadecimal.
                            Derived classes are
                            expected to return a text string which indicates the
                            type of the ring item.

` const virtual std::string  toString();`Returns a human readable stringified dump
                            of the body of the item.  In this case this is just
                            a byte by byte dump.  Derived classes are expected
                            to return something a bit more meaningful.  The
                            NSCLDAQ dumper, e.g. uses this string to
                            dump items it encounters.

` virtual void*  appendBodyData(const void*  pSrc, uint32_t  nBytes
                              );`Appends the `nBytes` bytes
                            of data pointed to by `pSrc`
                            to the ring item.  The data are placed where
                            the current body cursor is pointing.  The body cursor
                            is updated and the size recomputed.

This is equivalent to the following code fragment:

<a name="AEN1253"></a>```
  uint8_t* p = reinterpret_cast<uint8_t*>(getBodyCursor());
  memcpy(p, pSrc, nBytes);
  p += nBytes;
  setBodyCursor(p);
  updateSize();
  return p;

                            
```

The ring item object must have the capacity for the
                            additional bytes of data.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| RingItemFactoryBase | Up | CAbnormalEndItem (abstract) |
