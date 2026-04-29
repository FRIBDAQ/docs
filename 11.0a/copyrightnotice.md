|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.copyrightnotice"></a>CopyrightNotice

<a name="AEN37665"></a>## Name

CopyrightNotice -- Generate license/author credits.

<a name="AEN37668"></a>## Synopsis

```
#include <CopyrightNotice.h>
         
```

```
  static void Notice(std::ostream& out, const char* program, const char* version, const char* year);
```

<a name="AEN37701"></a>## Description

The `CopyrightNotice` class provides static
            methods for generating license notices and copyright strings
            when programs start.

<a name="AEN37705"></a>## Public member functions

` static void Notice(std::ostream& out, const char* program, const char* version, const char* year);`Outputs a copyright notice to the output stream
                `out`.  `program` is the
                name of the program. `version` is a
                version string, and `year` is the
                copyright year.

` static void AuthorCredit(std::ostream& out, char* program, ...);`Outputs credit for the authors.  The
                `out` and `program`
                parameters have the same meaning as for `Notice`.
                These parameters are followed by a null terminated variable length
                list of arguments that must all be const char*
                pointer to names of the authors.

<a name="AEN37745"></a>## EXAMPLES

Create a copyright notice on stderr.  This is from the
            `main` or other function that
            has access to the `argv` array:

<a name="AEN37750"></a>**Example 1. Creating a coypright notice on stderr**

```
CopyrightNotice::Notice(cerr, argv[0], "2.1", "2004");
                
```


Create an author credit on stderr for the authors Ron and Kanayo:

<a name="AEN37754"></a>**Example 2. Creating an author credit on stderr**

```
CopyrightNotice::AuthorCredit(cerr, argv[0], "Kanayo", "Ron", NULL);
                
```

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| URL | Up | CDAQShm |
