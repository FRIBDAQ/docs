<a name="AEN1"></a># <a name="AEN2"></a>mpiSpecTcl.

### <a name="AEN4"></a>Ron Fox


---

- **Table of Contents**
- 1. [Quick Start](https://github.com/FRIBDAQ/docs/tree/main/parallel/c13.md)
  - 1.1. [What is mpiSpecTcl](https://github.com/FRIBDAQ/docs/tree/main/parallel/c13.md#AEN27)
  - 1.2. [Checking for support of MPI parallelism.](https://github.com/FRIBDAQ/docs/tree/main/parallel/x34.md)
  - 1.3. [Environment variables you will need](https://github.com/FRIBDAQ/docs/tree/main/parallel/x48.md)
  - 1.4. [Running mpiSpecTcl in parallel mode](https://github.com/FRIBDAQ/docs/tree/main/parallel/x56.md)
  - 1.5. [Debugging mpiSpecTcl](https://github.com/FRIBDAQ/docs/tree/main/parallel/x80.md)
- 2. [Porting custom commands](https://github.com/FRIBDAQ/docs/tree/main/parallel/c103.md)
  - 2.1. [The command wrapper classes](https://github.com/FRIBDAQ/docs/tree/main/parallel/c103.md#AEN120)
  - 2.2. [Knowing the execution evironment](https://github.com/FRIBDAQ/docs/tree/main/parallel/x216.md)
  - 2.3. [Wrapping old argc, argv commands.](https://github.com/FRIBDAQ/docs/tree/main/parallel/x266.md)
- 3. [How mpiSpecTcl works in parallel mode.](https://github.com/FRIBDAQ/docs/tree/main/parallel/c362.md)
  - 3.1. [The MPI Process environment](https://github.com/FRIBDAQ/docs/tree/main/parallel/c362.md#AEN390)
  - 3.2. [mpiSpecTcl process roles](https://github.com/FRIBDAQ/docs/tree/main/parallel/x417.md)
    - 3.2.1. [World communicator rank 0 (MPI_ROOT_RANK)- the Root process](https://github.com/FRIBDAQ/docs/tree/main/parallel/x417.md#AEN431)
    - 3.2.2. [World communicator rank 1 (MPI_EVENT_SINK_RANK) - the event sink pipeline process](https://github.com/FRIBDAQ/docs/tree/main/parallel/x417.md#AEN447)
    - 3.2.3. [World communicator rank > 1 (MPI_FIRST_WORKER_RANK) - the event processing pipelines](https://github.com/FRIBDAQ/docs/tree/main/parallel/x417.md#AEN453)
  - 3.3. [MPI Pumps](https://github.com/FRIBDAQ/docs/tree/main/parallel/x462.md)
    - 3.3.1. [The Tcl command pump](https://github.com/FRIBDAQ/docs/tree/main/parallel/x462.md#AEN517)
    - 3.3.2. [The ring item pump](https://github.com/FRIBDAQ/docs/tree/main/parallel/x462.md#sec.ringpump)
    - 3.3.3. [The parameter pump](https://github.com/FRIBDAQ/docs/tree/main/parallel/x462.md#AEN571)
    - 3.3.4. [The Xamine gate pump](https://github.com/FRIBDAQ/docs/tree/main/parallel/x462.md#AEN610)
    - 3.3.5. [The gate trace pump](https://github.com/FRIBDAQ/docs/tree/main/parallel/x462.md#AEN624)
  - 3.4. [mpiSpecTcl initialization](https://github.com/FRIBDAQ/docs/tree/main/parallel/x641.md)
    - 3.4.1. [Root process (MPI_ROOT_RANK)](https://github.com/FRIBDAQ/docs/tree/main/parallel/x641.md#AEN678)
    - 3.4.2. [The event sink pipeline process (MPI_EVENT_SINK_RANK)](https://github.com/FRIBDAQ/docs/tree/main/parallel/x641.md#AEN712)
    - 3.4.3. [Worker processes (ranks at least MPI_FIRST_WORKER_RANK)](https://github.com/FRIBDAQ/docs/tree/main/parallel/x641.md#AEN732)
  - 3.5. [mipSpecTcl shutdown](https://github.com/FRIBDAQ/docs/tree/main/parallel/x746.md)
- A. [mpiSpecTcl  reference material](https://github.com/FRIBDAQ/docs/tree/main/parallel/a773.md)
  - A.1. [Utilities (3u)](https://github.com/FRIBDAQ/docs/tree/main/parallel/a773.md#AEN776)
    - [Globals.h](https://github.com/FRIBDAQ/docs/tree/main/parallel/r779.md) -- Describe MPI specific definitions in Globals.h
    - [TclPump.h](https://github.com/FRIBDAQ/docs/tree/main/parallel/r846.md) -- Utility definitions in TclPump.h
  - A.2. [Command jackets (3tcl)](https://github.com/FRIBDAQ/docs/tree/main/parallel/x887.md)
    - [CMPITclCommandAll](https://github.com/FRIBDAQ/docs/tree/main/parallel/r893.md) -- Jacket a command that runs in all ranks
    - [CMPITclCommand](https://github.com/FRIBDAQ/docs/tree/main/parallel/r948.md) -- Jacket a command that runs in other ranks
    - [CMPITclPackagedCommandAll](https://github.com/FRIBDAQ/docs/tree/main/parallel/r998.md) -- Wrap a packaged command that will execute in all processes
    - [CMPITclPackagedCommand](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1052.md) -- Jacket packagted commands to run in all but he root.
- B. [SpecTcl commands in the mpiSpecTcl environment](https://github.com/FRIBDAQ/docs/tree/main/parallel/a1102.md)
  - [applygate](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1108.md) -- Apply a gate to one or more spectra
  - [attach](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1145.md) -- Attach a data source to SpecTcl
  - [channel](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1188.md) -- Describe mpiSpecTcl implementation of the channel command.
  - [clear](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1222.md) -- MPI SpecTcl clear command
  - [evbunpack](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1265.md) -- mpiSpecTcl implementation of evbunpack
  - [filter](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1298.md) -- MPISpectcl Implementation of the filter command
  - [fit](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1363.md) -- Operation of fit command in mpiSpecTcl
  - [fold](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1406.md) -- THe fold command on mpiSpecTcl
  - [gate](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1439.md) -- Behavior of the gate command in mpiSpecTcl
  - [integrate](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1492.md) -- Integrate an area of interest
  - [mirror](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1515.md) -- List sthe mirrors being run
  - [parameter](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1534.md) -- Manipulate parametes.
  - [pman](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1585.md) -- Manipulate data analysis piplines
  - [project](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1656.md) -- Create projection spectra
  - [pseudo](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1684.md) -- Create and manipulate pseudo parameters
  - [remote](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1717.md) -- Allow scripts to know if they are operating remot of SpecTcl
  - [ringformat](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1734.md) -- Set the ring buffer fallback format version
  - [sbind](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1752.md) -- Bind spectra into the shared display memory
  - [shmemkey](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1791.md) -- Provide display shared memory identification
  - [shmemsize](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1809.md) -- Get the size of the spectrum pool of display shared memory
  - [specstats](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1827.md) -- Fetch spectrum over/underlow statistics
  - [version](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1847.md) -- Provide the SpecTcl version
  - [spectrum](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1864.md) -- Create and manipulate spectrum definitions
  - [sread](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1933.md) -- Read spectra from file
  - [start](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1963.md) -- start analysis from the current data source
  - [stop](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1977.md) -- Stop analyzing data from the data source
  - [swrite](https://github.com/FRIBDAQ/docs/tree/main/parallel/r1993.md) -- Write spectra to file
  - [treeparameter](https://github.com/FRIBDAQ/docs/tree/main/parallel/r2016.md) -- Manipulate the metadatak of tree parameters
  - [treevariable](https://github.com/FRIBDAQ/docs/tree/main/parallel/r2121.md) -- Manipulate Tree variables
  - [unbind](https://github.com/FRIBDAQ/docs/tree/main/parallel/r2169.md) -- Unbind spectra from display shared memory
  - [ungate](https://github.com/FRIBDAQ/docs/tree/main/parallel/r2198.md) -- Remove gate conditions from spectra
- C. [The MPI Tcl package](https://github.com/FRIBDAQ/docs/tree/main/parallel/a2217.md)
  - [mpi::send](https://github.com/FRIBDAQ/docs/tree/main/parallel/r2273.md) -- Allow rank 0 to execute scripts in other ranks.
- D. [XXUSB SpecTcl with MPI parallelism](https://github.com/FRIBDAQ/docs/tree/main/parallel/a2325.md)
  - D.1. [VMUSBSpecTcl](https://github.com/FRIBDAQ/docs/tree/main/parallel/a2325.md#AEN2348)

- **List of Examples**
- 1-1. [VERSION file for SpecTcls with MPI support](https://github.com/FRIBDAQ/docs/tree/main/parallel/x34.md#ex.version)
- 1-2. [mpirun exmaple](https://github.com/FRIBDAQ/docs/tree/main/parallel/x56.md#AEN62)
- 1-3. [Xterm per process and gdb per process](https://github.com/FRIBDAQ/docs/tree/main/parallel/x80.md#AEN92)
- 2-1. [Wrapping a command in `CMPITclCommand`](https://github.com/FRIBDAQ/docs/tree/main/parallel/c103.md#AEN141)
- 2-2. [Transparently wrapping commands by renaming the actual processor](https://github.com/FRIBDAQ/docs/tree/main/parallel/c103.md#AEN192)
- 2-3. [Implementing the replacement class](https://github.com/FRIBDAQ/docs/tree/main/parallel/c103.md#AEN208)
- 2-4. [Running commands only in workers](https://github.com/FRIBDAQ/docs/tree/main/parallel/x216.md#AEN263)
- 2-5. [Porting `CTCLProcessor` to 
                    `CTCLObjectProcessor` SpectrumCommand.h](https://github.com/FRIBDAQ/docs/tree/main/parallel/x266.md#AEN327)
- 2-6. [Porting `CTCLProcessor` to `CTCLObjectProcessor`
                    Marshalling arguments.](https://github.com/FRIBDAQ/docs/tree/main/parallel/x266.md#AEN340)
- 2-7. [Porting `CTCLProcessor` to `CTCLObjectProcessor`
                    substituting std::string for the result](https://github.com/FRIBDAQ/docs/tree/main/parallel/x266.md#AEN352)
- 3-1. [Worker top level pseudo code](https://github.com/FRIBDAQ/docs/tree/main/parallel/x417.md#AEN457)
- 3-2. [Sample Pump and API pseudo code](https://github.com/FRIBDAQ/docs/tree/main/parallel/x462.md#AEN473)
- C-1. [Loading the mpi Tcl package](https://github.com/FRIBDAQ/docs/tree/main/parallel/a2217.md#AEN2223)
- C-1. [Output the rank in each worker](https://github.com/FRIBDAQ/docs/tree/main/parallel/r2273.md#AEN2312)
- C-2. [Have workers output their roles and ranks](https://github.com/FRIBDAQ/docs/tree/main/parallel/r2273.md#AEN2317)
- C-3. [A send command that clears all spectra](https://github.com/FRIBDAQ/docs/tree/main/parallel/r2273.md#AEN2320)
- D-1. [VMUSB configuration](https://github.com/FRIBDAQ/docs/tree/main/parallel/a2325.md#AEN2352)

---

|  |  |  |
| --- | --- | --- |
|  |  | Next |
|  |  | Quick Start |
