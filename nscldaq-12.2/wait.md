|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN114000"></a>wait

<a name="AEN114004"></a>## Name

wait -- Wait/reap for subprocess completion

<a name="AEN114007"></a>## Synopsis

```
package require Wait
             
```

```
-pid
```

<a name="AEN114017"></a>## DESCRIPTION

In unix in most cases child processes don't completely disappear
            when they exit.  After exit, they can deliver status information
            to their parent.  The Unix `wait`(2) and
            `waitpid`(2) functions are the mechanism
            by which the parent process obtains this status.
            Obtaining child status is also sometimes called "reaping".

In most cases, child processes created by Tcl's
            **exec** or **open** commands
            are reaped by the interpreter's event handling subsystem.  Subprocesse
            started by other means are not automatically reaped and this
            **wait** command can be used
            to perform that task.

The command returns a two element list containing the
            process id of the process that satisfied the wait and
            the status code returned by the process.  If no matching process
            exited, the list contains a pair of zeroes (list 0 0).
            Any errors returned from the underlying wait system service
            result in a POSIX like Tcl error.

<a name="AEN114028"></a>## OPTIONS

Note that all options are optional.  By default, the command
            blocks until the next



`-pid` pidSpecifies what to wait for.



- A value of -1 waits for the
                                  next exiting child process.  This the
                                  default when no `-pid` option
                                  is supplied.
- A value greater than zero waits for only the
                                  process with the specified PID to exit.
- A value of 0 waits for any process in the
                                  process group of which we are a member to exit.
- A value less than zero waits for any process
                                  in the process group that is the absolute value
                                  of `pid`.

`-poll`If this option is provided, the command returns
                        immediately.  Otherwise it blocks until a process matching
                        the `-pid` specification exits.  This
                        is equivalent to the
                        WNOHANG flag described in the
                        `wait`(2) manpage.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Utils | Up | Pipe |
