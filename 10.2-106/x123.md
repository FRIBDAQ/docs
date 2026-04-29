|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 1. Introduction | Next |


---

# <a name="AEN123"></a>1.2. Overview of ring buffer utilities

This section will give a brief overview of some of the ring buffer
            utilities.  Please refer to the remainder of this documentation
            for detailed descriptions and reference material for each utility.
            This list is only a selection of utilities.



ringbufferThis utility allows you to create, re-initialize, delete  and
                        monitor the status of ringbuffers.  Normally you don't
                        have to create ring buffers as producer frameworks
                        will create them if they don't already exist.

dumperProvides a simple textual formatted dump of the buffers.
                    If you want more advanced formatting, you can use
                    the tkdumper application.
                    By contrast with dumper,
                    tkdumper can be extended with
                    plugins in such a way that it can provide a human readable
                    formatted view of each event and the packets within the
                    event.

eventlogPerforms native mode event loggging.  In this mode,
                    event file segments consists of streams of ring buffer items.
                    This is the default event logger run by the
                    ReadoutShell (see below), if you
                    want to log data in a format compatible with spectrodaq based
                    DAQ versions (version 8.x and earlier), use
                    eventlog-compat

ReadoutShellProvides a GUI wrapper around a readout program that is
                        started in a remote system.

ringselectorProvides a flexible ringbuffer consumer that pipes
                    the ring items it gets to standard output.  This
                    can be run over a pipe into your program or as the
                    first stage of a pipeline that transforms data before
                    providing it to an application (eventlog-compat
                    is actually a pipeline with ringslector as the source
                    piping through compatibilitybuffer
                    and then on to compatibilitylogger).

ringtostdoutAccepts data from a ring and pipes it to stdout.  This is
                    the server side of the pipeline between systems when you are
                    setting up a proxy ring.  It can also be used as the first
                    stage of a pipeline to process data from  a ring.

ScalerDisplayProvides a display of scaler event data.  This application
                    is highly configurable.  It can accept an arbitrary number
                    of scalers and format any number of pages as tabs in a notebook.
                    Strip charts of selected scalers are also supported.

stdintoringAccepts data on stdin and puts it in a ring buffer.
                    This is the client side of the data pipeline that sets up
                    a proxy ring.

spectcldaqPipe data source for SpecTcl software that has not yet
                    been ported to ring buffer data format.  This accepts data
                    from a ring and outputs it on stdout in nscldaq-8.x format.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Introduction | Up | Documentation roadmap |
