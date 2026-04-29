|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.os"></a>Os

<a name="AEN42548"></a>## Name

Os -- Operating system interfaces.

<a name="AEN42551"></a>## Synopsis

```
Os
```

<a name="AEN42608"></a>## DESCRIPTION

The `Os` class provides a set of static methods
        that abstract some simple operating system interfaces.

<a name="AEN42612"></a>## METHODS



` static  std::string  whoami()();`Returns the name of the user that is currently running
                    the process.

` static  bool  authenticateUser( std::string  sUser,  std::string  sPassword);`Given a user name;  `sUser` and a
                    password; `sPassword`, returns
                    true if that username and password
                    represent valid login credentials to the system,
                    false if not.

` static  int   usleep( useconds_t  usec);`Pauses the caller for `usec`
                    microseconds. 0 is returned if
                    the sleep was successful and for the full requested period.
                    -1 is returned if not and `errno`
                    has an error code.  If `errno` is
                    EINTR 
                    the sleep was interrupted by a signal and the interval
                    was not complete.  Other values of `errno`represent errors.

` static  int   blockSignal( int  sigNum);`Blocks the signal specified by `sigNum`.
                    If the signal can be blocked it will no longer be processed
                     by the calling process.  The method returns
                     0 on success and -1
                     on failure.  If the call fails, `errno`
                     is a code that describes why the operation failed.

` static  int   checkStatus( int status , int checkStatus,   std::string  msg);`Compares `status` with
                    `checkStatus` if not equal,
                    a `std::runtime_error` is thrown
                    with `msg` as the message string.
                    The function returns the value of `status`.

` static  int   checkNegativeStatus( int  returnCode);`If `returnCode` is negative,
                    the method throws a `CErrnoException`.
                    The exception string is the error string that corrersponds
                    to the `returnCode` as if
                    `returnCode` were a valid
                    `errno` error value.

On success, the value of `returnCode`
                    is returned.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| io | Up | CDAQShm |
