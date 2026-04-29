|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 30. Compatibility utilities | Next |


---

# <a name="AEN7464"></a>30.5. BufferToRing

Sometimes you will have to take emitters of NSCL Buffered data and
            translate them into ring items.  BufferToRing is a filter that
            takes NSCL event buffers on stdin and emits
            ring items on stdout.  This allows you to pipe
            old event files into a ring buffer SpecTcl.  With the assistance
            of stdintoring you can also pipe old data into a ringbuffer.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Convenience scripts | Up | Providing EPICS channel information to Tcl Servers |
