|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN102515"></a>Pipe

<a name="AEN102519"></a>## Name

Pipe -- Make a unix pipe

<a name="AEN102522"></a>## Synopsis

```
            package require Wait
                             
            set fds [Pipe]
set readpipe [lindex $fds 0]
set writepipe [lindex $fds 1]
                             

        
```

<a name="AEN102528"></a>## DESCRIPTION

Produces a unix pipe and binds both the readable and writeable
            sides of the pipe to Tcl channels.  One use case for this is
            to setup a communications channel between Tcl threads (see
            **thread::trasnfer** in the Tcl thread package).

Other use cases include ssetting up pipes to capture output, or error
            of intermediate stages of Tcl  pipelines created with
            **exec** or **open**.

This command never failas.  It produces a two element list.
            The first element of the list is the read side of the pipe and
            the second the write side.  This matches the implementation of
            the Unix `pipe`(2) system service.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| wait | Up | ppid |
