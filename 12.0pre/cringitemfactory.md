|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="daq3_cringitemfactory"></a>CRingItemFactory

<a name="AEN31142"></a>## Name

CRingItemFactory -- Upcast ring items to specific ring item objects.

<a name="AEN31145"></a>## Synopsis

```
#include <CRingItemFactory.h>
            
```

```
CRingItemFactory
```

<a name="AEN31174"></a>## DESCRIPTION

`CRingItem`
             provides a set of static methods that
             allow you to upcast ring items to actual
             underlying ring item types.  In general you
             will validate the item type via
             `isKnownItemType`
             and then invoke one o f the 
             `createRingItem`
             methods.   Finally if you need to
             use an item specific methods, you would do a
             reinterpret_cast to 
             the correct subclass of `CRingItem`.

See METHODS below for more
             information about these functions.

<a name="AEN31184"></a>## METHODS



` static CRingItem* createRingItem(const CRingItem& item);`Creates the appropriate ring item
                       given a reference to a base class
                       ring item.  A pointer is returned
                       to the resulting object.  The
                       object is dynamically allocated
                       and therefore must be 
                       deleted by the caller.

` static CRingItem* createRingItem(static void* pItem);`Creates the appropriet ring item
                          given a pointer to storage that
                          is believed to contain a 
                          RingItem struct
                          as defined in 
                          DataFormat.h

The only difference between this
                          and the previous method is the
                          parameter type.

` static bool 
                    isKnownItemType
                (const void* pItem);`If `pItem`
                           points to a 
                           RingItem
                           of a type known to the factory,
                           this method returns
                           true,
                           otherwise, false

The creational methods of the
                           factory will return a generic
                           ring item if they don't recognize
                           the ring type.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CDataSourceFactory" | Up | CDataSink |
