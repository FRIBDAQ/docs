|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 2. The Ring Buffer | Next |


---

# <a name="AEN132"></a>2.4. Ring buffer utilities

This section will give a brief overview of some of the ring buffer
      utilities.  Please refer to the remainder of this documentation
      for detailed descriptions and reference material for each utility.
      This list is only a selection of utilities.



ringbufferThis utility allows you to create, re-initialize, delete  and
            monitor the status of ringbuffers.  Normally you don't have to
            create ring buffers as producer frameworks will create them if they
            don't already exist. See the [[r12646]] for more information.

dumperProvides a simple textual formatted dump of the buffers.  If you
            want more advanced formatting, you can use the
            tkdumper application.  By contrast with
            dumper,
            tkdumper can be extended with plugins in
            such a way that it can provide a human readable formatted view of
            each event and the packets within the event. See [[c7470]] and [[r13495]] for more information.

eventlogPerforms native mode event loggging.  In this mode, event file
            segments consists of streams of ring buffer items. See [[c7534]] and [[r13589]] for more information.

ringselectorProvides a flexible ringbuffer consumer that pipes the ring items
            it gets to standard output.  This can be run over a pipe into your
            program or as the first stage of a pipeline that transforms data
            before providing it to an application. Unlike other processes, this
            will never introduce flow control and is suitable for sampling
            applications like SpecTcl. See [[c7865]] and [[r13843]] for more information.

ringtostdoutAccepts data from a ring and pipes it to stdout.  This is the server
            side of the pipeline between systems when you are setting up a proxy
            ring.  It can also be used as the first stage of a pipeline to
            process data from  a ring. See the [[r12770]] for more information.

ScalerDisplayProvides a display of scaler event data.  This application is highly
            configurable.  It can accept an arbitrary number of scalers and
            format any number of pages as tabs in a notebook.  Strip charts of
            selected scalers are also supported. See [[c4589]] and [[r13187#manpage.scalerdisplay]] for more information.

stdintoringAccepts data on stdin and puts it in a ring buffer.  This is the
            client side of the data pipeline that sets up a proxy ring. See the [[r12834]] for more information.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Proxy Rings, Ring Masters, and Network Transparency | Up | NSCLDAQ Data Format : The Ring Item |
