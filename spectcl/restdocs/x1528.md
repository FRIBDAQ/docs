|  |  |  |
| --- | --- | --- |
| SpecTcl REST plugin |
| Prev | Chapter 3. REST requests supported. | Next |


---

# <a name="AEN1528"></a>3.22. Access the ringformat command (new in 5.5)

The ringformat command can be accessed via URLs of the form

<a name="AEN1531"></a>**http://host:port/spectcl/ringformat?major=majvsn[&minor=minor]
               **

The major query parameter sets the major version,
            while the  minor sets the minor version.  Note
            that the minor version defaults to 0 which,
            since the format of ring items is not allowed to change within a
            major version of NSCLDAQ is normally correct.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Access to the sread command (new in 5.5) | Up | Accessing the unbind command (new in 5.5) |
