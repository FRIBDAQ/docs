|  |  |  |
| --- | --- | --- |
| mpiSpecTcl. |
| Prev | Chapter 3. How mpiSpecTcl works in parallel mode. | Next |


---

# <a name="AEN417"></a>3.2. mpiSpecTcl process roles

In the previous section MPI was described.  Recall that the computing model in MPI is 
                a data parallel model.  While in mpiSpecTcl, event processing is fully data parallel, there
                are otherr things going on.  As such, mpiSpecTcl's computing model is a mix of functionally
                distributed processing and data parallel processing.  Each process in mpiSpecTcl has a specific
                role.  The world communicator rank is used by each process to select the code that actually runs.
                Each process fulfils one of three roles:



1. Main or root process
2. Event sink pipeline
3. Worker - event processing pipeline.

mpiSpecTcl has only one root process, and one event sink pipeline process but can have 
                any number of worker processes.  As converting raw parameters is, for complex analyses,
                the rate determining step, the data parallelism of the worker processes is where the
                speed gains are.

Symbolic definitions for the MPI role ranks are in Core/Globals.h which
                is also installed in the include subdirectory of the SpecTcl installation
                tree.

## <a name="AEN431"></a>3.2.1. World communicator rank 0 (MPI_ROOT_RANK)- the Root process

The root process is responsible for:



- Running the interactive Tcl interpreter.  Note that all processes run a
                          Tcl interpreter, however onlyi the root one actually takes input from stdin
                          and runs GUIs.    In
- Data sources are opened in this process role and ring items are distributed to the
                          event processing pipeline (worker) )rocesses.  Ring items of type PHYSICS_EVENT
                          are transmitted to idle workers and all other ring item types are broadcast to all workers.
- When SpecTcl has been told to run a ReST server, the root process runs that server.

Note that the SpecTclInit.tcl is processed by all ranks
                    and the SpecTclRC.tcl initialization file is only processed in the
                    root process.  This means, however that SpecTcl commands in those scripts 
                    *will* be processed in all processes.

## <a name="AEN447"></a>3.2.2. World communicator rank 1 (MPI_EVENT_SINK_RANK) - the event sink pipeline process

The event sink pipeline is sent the outputs of the event processing pipelines.
                    Note that, since event processing times may vary from event to event, the order in
                    which events are received by the event sink pipeline is non-deterministic.

In addition any displayer program is started by the event sink pipeline and the
                    shared memory  into which spectra can be bound is created by this process.

The mirror server is also run by this process if mirroring is required.

## <a name="AEN453"></a>3.2.3. World communicator rank > 1 (MPI_FIRST_WORKER_RANK) - the event processing pipelines

This role runs the event processing pipeline.  Transparent to user code, the worker
                    processe run a loop with a simplified structure that looks like:

<a name="AEN457"></a>**Example 3-1. Worker top level pseudo code**

```
do until exit:
    Get an event 
    Process the event in the user event processing pipeline
    Send resulting parameters to the event sink pipeline.
                    
```

The actual mechanics of event distribution to the workers is described in 
                    [[x462#sec.ringpump]]

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| How mpiSpecTcl works in parallel mode. | Up | MPI Pumps |
