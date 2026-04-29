|  |  |  |
| --- | --- | --- |
| NSCLDAQ Unified Format Library |
| Prev |  | Next |


---

# <a name="AEN269"></a>Format Selector

<a name="AEN273"></a>## Name

Format Selector -- Select Specific Format Factory

<a name="AEN276"></a>## Synopsis

```
#include <NSCLDAQFactorySelector.h>

namespace FormatSelector {
    enum SupportedVersions {v10, v11, v12};

    RingItemFactoryBase& selectFactory(SupportedVersions version);
    RingItemFactoryBase& selectFactory(CDataFormatItem& item);


}


                
```

<a name="AEN278"></a>## DESCRIPTION

The definitions in the FormatSelector
                    namespace provide mechnisms to select  specific format factory
                    either from an explicit format specifier or from a data format item.
                    Note that data format items appear in NSCLDAQ-11 and later.

The format factories instantiated by these functions are cached
                    for later lookup.  This implies that:



1. Ownership of the factories continues to reside with this
                             module.  Deleting a factory returned from this API
                             will result in undefined, possibly fatal, behavior.
2. Several attempts to get a factory reference for the same
                             format version will return references to the same factory
                             instance.

<a name="AEN288"></a>## DATA TYPES

The FormatSelector::SupportedVersions enum
                    is a type that is used as an NSCLDAQ version selector.

<a name="AEN292"></a>## API

Note that while all functions live in the
                    FormatSelector namespace
                    this is not shown in the function list below for the sake
                    of brevity.



` ::RingItemFactoryBase& selectFactory(SupportedVersions version);`Returns a reference to a ring item factory that is
                            suitable for creatig ring items for the NSCLDAQ
                            version selected by `version`.
                            The factory continues to be owned by the selection
                            subsystem and must *not* be deleted
                            by the caller.

A cache of factories ensures that several attempts
                            to obtain a factory for the same version will return
                            references to the same factory.

` ::RingItemFactoryBase&  selectFactory(CDataFormatItem&  item);`Given a reference to a data format item from any
                            version of NSCLDAQ that can produce these, provides
                            a factory for the version of NSCLDAQ indicated by that
                            item.  This wraps the prior overload for
                            `selectFactory` so everything
                            described above about the returned reference holds for
                            this one.

If a version is selected which is somehow not supported,
                    `std::invalid_argument` is thrown by
                    the `selectFactoryMethods` above.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Reference pages | Up | RingItemFactoryBase |
