|  |  |  |
| --- | --- | --- |
| SpecTcl Programming Reference. |
| Prev |  | Next |


---

# <a name="AEN12583"></a>RingFormatHelper Factories

<a name="AEN12587"></a>## Name

CRingFormatelperFactory, CRingFormatHelperCreator, CRingFormatHelper10Creator, CRingFormatHelper11Creator --

<a name="AEN12593"></a>## Synopsis

```
#include <CRingFormatHelperFactory.h>

class CRingFormatHelperFactory {
    CRingFormatHelperFactory();
    CRingFormatHelper* create(uint32_t major, uint32_t minor);
    CRingFormatHelper* create(void* pFormatItem);
    
    void addCreator(
        uint32_t major, uint32_t minor, const CRingFormatHelperCreator& creator
    );
    void removeCreator(uint32_t major, uint32_t minor);

};
        
```

```
#include <RingFormatHelperCreator.h>

class CRingFormatHelperCreator
{   
public:
    CRingFormatHelperCreator() {}
    virtual CRingFormatHelperCreator* clone() const = 0;
    virtual CRingFormatHelper*        create() = 0;
};
        
```

```
#include <RingFormatHelper10Creator.h>

class CRingFormatHelper10Creator : public CRingFormatHelperCreator
{
public:
    CRingFormatHelper10Creator() {}
    virtual CRingFormatHelperCreator* clone() const;
    virtual CRingFormatHelper*        create();
};
        
```

```
#include <RingFormatHelper10Creator.h>

class CRingFormatHelper10Creator : public CRingFormatHelperCreator
{
public:
    CRingFormatHelper10Creator() {}
    virtual CRingFormatHelperCreator* clone() const;
    virtual CRingFormatHelper*        create();
};
        
```

<a name="AEN12598"></a>## DESCRIPTION

This complex of classes is responsible for selecting the
            correct Ring format helper.  It follows the pattern of an extensible
            factory.  `CRingFormatHelperFactory` is the
            factory class, while the classes that are derived from
            `CRingFormatHelperCreator` provide
            creators that match ring item format information with
            the ability to create the appopriate helper.

In this man page, we're only going to document the methods
            of `CRingFormatHelperFactory` and the
            creator base class of `CRingFormatHelperCreator`.

<a name="AEN12606"></a>## `CRingFormatHelperFactory METHODS`



`  CRingFormatHelperFactory();`Constructor.  Note the constructor creates a factory
                        that has no creational objects.

`   CRingFormatHelper*  create( uint32_t  major,  uint32_t  minor);`Attempts to create a ring format helper that understands
                        the format version specified by the
                        `major` and
                        `minor` versions specified.
                        If there is no creator willing to make a helper for the
                        specified format version, a null pointer is returned.

The return value is a pointer to a dynamically allocated helper
                        that must eventually be freed by delete

`   CRingFormatHelper*  create( void*  pFormatItem);`Given a ring format item, extracts the version information
                        from it and attempts to return a pointer to a format
                        helper.  If no creators have been registered to create
                        a helper for the resulting version a null pointer is
                        returned.

The pointer returned is to a dynamically allocated
                        `CRingFormatHelper` object that
                        must eventually be destroyed with delete.

`   void  addCreator( uint32_t  major ,  uint32_t  minor, const  CRingFormatHelperCreator&  creator);`Registers `creator` as a creational
                        object that can create a helper for
                        the version specified by `major`
                        and `minor`.  Note that the
                        `creator` is cloned so its lifetime
                        is not important.

`   void  removeCreator( uint32_t  major,  uint32_t  minor);`Removes/deletes the creator associated
                        with the format level specified by
                        `major` and
                        `minor`.  Attempts to remove
                        a creator for a format version level that has not been
                        registered are silently ignored.

<a name="AEN12698"></a>## RingFormatHelperCreator METHODS



` virtual  const = 0 CRingFormatHelperCreator*  clone();`Returns a pointer to a dynamically allocated
                        copy of `*this`.  Typically this can be done
                        by defining a copy constructor and using it as a parameter
                        of new.

` virtual  = 0 CRingFormatHelper* create();`Creates a dynamically allocated helepr.  The factory
                        will have matched a version specification with the helper
                        registered for it.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CRingFormatHelper, CRingFormatHelper10, CRingFormatHelper11 | Up | CParameter |
