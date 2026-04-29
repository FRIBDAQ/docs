|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.cstringinteractor"></a>CStringInteractor

<a name="AEN53427"></a>## Name

CStringInteractor -- Provide an interactor that processes strings.

<a name="AEN53430"></a>## Synopsis

```
#include <CStringInteractor.h>
         
```

```
  CStringInteractor(const std::string& am_sString);
```

<a name="AEN53492"></a>## Description

String interactors allow you to treat strings gotten by whatever means
            as sources for interactors.  Note that writes to a string interactor
            are not errors, they just don't do anything.  This makes string interactors
            behave consistently if used as interactive entitites.

While string interactors behave exactly like any other interactor,
	    they have additional member functions that recognize their string
	    nature.

<a name="AEN53496"></a>## Public member functions

`  CStringInteractor(const std::string& am_sString);`Constructs a string interactor given a string
		   `am_sString`. The string
                   will be the data 'read' by the interactor.

`  CStringInteractor(const CStringInteractor& aCStringInteractor);`Constructs a string interactor that is an exact state
		   duplicate of 
		   `aCStringInteractor`.
		   The duplication extends not only to the string but to the
		   position within the string from which data will be returned
		   to satisfy read operations (the cursor).

`  ~CStringInteractor();`Releases all storage and resources required by the
	       interactor prior to its finaly destruction.

` const int operator==(const CStringInteractor& aCStringInteractor);`Assignment operator.  The object will become an exact duplicate
	       of the `aCStringInteractor`.
	       This duplication extends to the cursor.

` const std::string getString();`Informational method that returns the full string managed by
	       the interactor.

` const int getReadCursor();`Informational method that returns the read cursor.  The read
	       is the offset into the string managed by the interactor from
	       which the next read will be satisfied.  If, for example,
	       an interactor `*interactor`
	       was constructed on the string
		   `astring`,
	       the first character of the next read will be
               `astring[interactor->getReadCursor()]`

` void Rewind();`Resets the read  cursor to zero, allowing the string to be
		   re-read.

` virtual int Read(UInt_t nBytes, void* pBuffer);`Returns data from the string.  At most
		   `nBytes`
	       of data are read beginning at the read cursor.  If there are
		   fewer, than `nBytes` of data left in
		   the string, the entire remainder of the string is read.
		   The data is copied from the string to 
		   `pBuffer`.
		   The number of bytes actually read is returned as the
		   method's function value.

After the read has been completed, the read cursor is advanced
	       by the number of bytes returned.  If there are no more bytes
		   available in the string, the function will return
		   0 and no data will be transfered to 
		   `pBuffer`

` virtual int Write(UInt_t nBytes, void* pBuffer);`This function simply returns the value of
	       `nBytes`.  This simulates successful
	       completion of the write, although no data will actually be
		   transferred.

<a name="AEN53577"></a>## EXAMPLES

This example shows how to determine that an interactor is a string
	    interactor and if so, rewind it:

<a name="AEN53580"></a>**Example 1. Calling `CStringInteractor` specific
         members**

```
CInteractor*       pAnInteractor = getInteractor();
...
CStringIteractor*  pString       =
         dynamic_cast<CStringInteractor*>(pAnInteractor);
if (pString) {
   pString->Rewind(); 
}
	     
```

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CInteractor | Up | CFdInteractor |
