|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.ctclaccesslistcheck"></a>CTclAccessListCheck

<a name="AEN54287"></a>## Name

CTclAccessListCheck -- Authenticate against a Tcl List.

<a name="AEN54290"></a>## Synopsis

```
#include <TclAccessListCheck.h>
         
```

```
  CTclAccessListCheck (Tcl_Interp* pInterp, const std::string& rName);
```

<a name="AEN54322"></a>## Description

This authenticator is intended to be used in conjunction with
            Tcl scripts and Tcl servers.  The authenticator uses a Tcl variable
            that contains a list of  values.  The entity that desires service
            must present one of the values in that list as its credential.

<a name="AEN54325"></a>## Public member functions

`  CTclAccessListCheck (Tcl_Interp* pInterp, const std::string& rName);`Constructs a Tcl Access list authenticator.
                `pInterp`
                is the interpreter handle pointer.  This will be wrapped
                in a
                `CTCLInterpreter`
                object.  For more information about the CTCLInterpreter class, 
                see the
                [[r58156]].

The `rName` parameter is the name of the
                TCL variable that contains the list of allowed credentials. Note that
                the list does not yet need to have been created and, in fact, the
                variable
                `rName`
                need not yet exist.  The variable and list only need to exist
                at authentication time.

`  ~CTclAccessListCheck();`Releases any resources allocatd by the authenticator as it's destroyed.

` const CTCLVariable* getVariable();`Returns a pointer to the
                `CTCLVariable`
                that wraps the Tcl variable.  For more information about
                `CTCLVariable`
                objects, see
               the
                [[r58936]].

` const CTCLInterpreter* getInterpreter();`Retrieves a pointer to the Tcl Interpreter wrapped in a
                `CTCLInterpreter`
                object.

` virtual Bool_t Authenticate(CInteractor& rInteractor);`Uses the
                `rInteractor`
                to fetch a credential from the requestor.  If the credential is
                a member of the list in the Tcl variable with which the authenticator
                was constructed, this method will return
                kfTRUE
                If not,
                kfFALSE

<a name="AEN54372"></a>## Types and public data

`CTCLInterpreter`
            and
            `CTCLVariable`
            are objects that are part of the Tcl++ library.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CUnixUserCheck | Up | CAccessListCheck |
