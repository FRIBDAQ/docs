|  |  |  |
| --- | --- | --- |
| mpiSpecTcl. |
| Prev | Chapter 3. How mpiSpecTcl works in parallel mode. | Next |


---

# <a name="AEN641"></a>3.4. mpiSpecTcl initialization

Note that the code described here is in the file Core/TclGrammerApp.cpp.
                SpecTcl initialization in the MPI environment requires that the program:



- Verify that the program is runnig in paralle mode 
                      (see `CTclGrammerApp`::`run`).
- Initialize MPI (`CTclGrammerApp`::`MPIAppInit`)
- Determine the world rank of the process (`CTclGrammerApp`::`MPIAppInit`)
                      and verify there are sufficient processes in the application to fulfil all roles.
- Split the world communicator, creating the ring item communicator and the
                      gate communicator, used by the pumps for those
                      data (`CTclGrammerApp`::`MPIAppInit`).
- Do application common and role specific initialization
                      (in `CTclGrammerApp`::`AppInit()`).

The common and per-role initialization begins in 
                `CTclGrammerApp`::`AppInit()`
                which was the application initialization function in SpecTcl prior to version 7.0.
                It creates a  Tcl interpreter,  invokes 
                `CTclGrammerApp`::`operator()`, which does the
                bulk of the initialiation and then, if the process is the root process, sets up a Tcl
                event loop for the process which can take commands from stdin
                If the process is not the root process, closes the stdin
                Tcl channel, starts the command pump and runs an event loop.  This is done
                in the static function `setupSlaveInterpreter`.

The bulk of initialization is driven by 
                `CTclGrammerApp`::`operator()`.  This is the virtual 
                method that is considered the entry point to the SpecTcl applicatikon.  It 
                invokes a bunch of virtual methods which provide extension points for user code.  
                Some of the methods are unconditionally invoked while others are invoked conditionally 
                depending on the process world rank.  In the subsection that follows we'll delve into
                the operations that are conditionally done on the basis of process role (world rank).

The emphasis is on initializations that are done in each process but not all
                processes and intializations that are not done in this process.  The latter is
                important in determining if you have specialized application specific code that
                requires modification to run in mpiSpecTcl.

## <a name="AEN678"></a>3.4.1. Root process (MPI_ROOT_RANK)

The root process:



- Does not invoke `CreateHistogrammer`,
                          Nor does it invoke `CreateDisplays`.  It does, therefore
                          invoke `startGatePump` to receive information about gates
                          transmitted to the event sink pipeline process by Xamine if it is chosen
                          to visualize histograms.
- If the SpecTclInit.tcl script specified a `HTTPDPort`,
                          The root process starts and runs the ReST server.
- The displayer is not selected, nor is it started by the Root process
- `atexit` is used to setup `MPIExitHandler`
                          to run as the program is exiting in all process roles.  See
                          [[x746]] for information
                          about what this exit handler does.
- The test data source is only setup in the root process.  This allows test data to
                          be generated and distributed.
- The analyzer is created and the ring item buffer decoder is selected. The analyzer is used
                          both in processing events from the data source in the root process and in the dispatching of
                          events to the event processing pipelines in the workers.
- The run control subsystem is setup.  This supports starting and stopping data 
                          analysis.  The Root process manages data sources data distribution.  In
                          the worker and event sink processors, data are pumped into the event loops
                          of their interpreters.
- The SpecTclRC.tcl script(s) are sourced.  This is only 
                          done in the root process as often these scripts build graphical user interfaces.
                          by this time, the other processes are running the Tcl pump so any
                          SpecTcl command extensions run in this script will be appropriately distributed
                          to the other processes.
- The acknowledgements and the VERSION file are printed out.

Note that this implies there is not histogramer object in the root process.
                    Nonetheless, dictionaries of parameter, spectrum, gates and treevariables are maintained
                    and can be accessed via the API provided by the `SpecTcl`
                    singleton class.

## <a name="AEN712"></a>3.4.2. The event sink pipeline process (MPI_EVENT_SINK_RANK)

`TclGrammerApp`::`operator()`
                    does the following for the event sink pipeline.



- The histogramer is created as is the displayer.
- The mirror server is started.
                          This is done
                          in `TclGrammerApp`::`CreateDisplays`
                          which is only called in the event sink rank.
- The parameter pump is started. Note that it is the call to 
                          `startHistogramPump` that does this.
- `atexit` is used to establish `MPIExitHandler`
                          to run at process exit to shutdown the pumps and perform other cleanup activities.

## <a name="AEN732"></a>3.4.3. Worker processes (ranks at least MPI_FIRST_WORKER_RANK)

`TclGrammerApp`::`operator()` does
                    the following in processes that are workers.



- An analyzer is created to dispatch events received in its ring item pump
                          to the analysis pipeline.  The analyzer created in this way, 
                          forwards parameters unpacked and/or computed by physics event ring items
                          to the event sink process for histograming etc.
- A buffer decoder is created (for ring items) which will be used to pick apart the
                          ring items that are sent to the workers.
- The analysis pipeline is set up via user code in the `CreateAnalysisPipeline`
                          and the ring item pump is started to pump events distributed to the worker to the event loop from 
                          which they are dispatched to the analysis pipeline.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| MPI Pumps | Up | mipSpecTcl shutdown |
