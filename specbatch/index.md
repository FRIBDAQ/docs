[← MPISpecTcl - Massively parallel SpecTcl.](https://github.com/FRIBDAQ/docs/tree/main/specbatch/c74.md) | [Home](https://github.com/FRIBDAQ/docs/tree/main/Home.md) | [analysissink →](https://github.com/FRIBDAQ/docs/tree/main/specbatch/r641.md)

---

<a name="AEN1"></a># <a name="AEN2"></a>Batch SpecTcl (5.2 and later)

### <a name="AEN4"></a>Ron Fox


---

- **Table of Contents**
- 1. [Introduction](https://github.com/FRIBDAQ/docs/tree/main/specbatch/c13.md)
- 2. [Serial batch SpectTcl](https://github.com/FRIBDAQ/docs/tree/main/specbatch/c37.md)
  - 2.1. [Incorporating batch SpecTcl in to a Tcl interpreter](https://github.com/FRIBDAQ/docs/tree/main/specbatch/c37.md#AEN52)
  - 2.2. [Commands supported by batch SpecTcl](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x66.md)
  - 2.3. [How Batch SpeTcl analyzes data](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x192.md)
  - 2.4. [Creating a loadable package for the event analysis pipeline](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x230.md)
  - 2.5. [A simple analysis script.](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x342.md)
- 3. [MPITcl - an enhanced Tcl interpreter](https://github.com/FRIBDAQ/docs/tree/main/specbatch/c406.md)
  - 3.1. [MPI Concepts](https://github.com/FRIBDAQ/docs/tree/main/specbatch/c406.md#AEN422)
  - 3.2. [How MPI Concepts map to MPITcl](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x431.md)
  - 3.3. [The mpi::mpi command ensemble.](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x447.md)
  - 3.4. [Running MPITcl (NSCL/FRIB specific)](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x501.md)
- 4. [MPISpecTcl - Massively parallel SpecTcl.](https://github.com/FRIBDAQ/docs/tree/main/specbatch/c549.md)
  - 4.1. [The mpispectcl package](https://github.com/FRIBDAQ/docs/tree/main/specbatch/c549.md#AEN562)
  - 4.2. [Parallel models for SpecTcl](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x570.md)
  - 4.3. [Serial reader parallel worker example.](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x583.md)
- A. [Reference (man) pages](https://github.com/FRIBDAQ/docs/tree/main/specbatch/a635.md)
  - A.1. [Batch SpecTcl](https://github.com/FRIBDAQ/docs/tree/main/specbatch/a635.md#AEN638)
    - [analysissink](https://github.com/FRIBDAQ/docs/tree/main/specbatch/r641.md) -- Establish a data distributor to the anlaysis pipeline
    - [analyze](https://github.com/FRIBDAQ/docs/tree/main/specbatch/r656.md) -- Begin analysis.
    - [filesource](https://github.com/FRIBDAQ/docs/tree/main/specbatch/r672.md) -- Establish a data getter from a file.
    - [CDataGetter](https://github.com/FRIBDAQ/docs/tree/main/specbatch/r690.md) -- Base class for data getters.
    - [CDataDistributor](https://github.com/FRIBDAQ/docs/tree/main/specbatch/r732.md) -- Data Distribution base class.
  - A.2. [MPITcl](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x746.md)
    - [mpi::mpi](https://github.com/FRIBDAQ/docs/tree/main/specbatch/r749.md) -- Command ensemble for MPI under tcl.
    - [MPITcl binary data.](https://github.com/FRIBDAQ/docs/tree/main/specbatch/r853.md) -- Receiving binary data in compiled MPITcl extensions
  - A.3. [MPI SpecTcl](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x882.md)
    - [mpisource](https://github.com/FRIBDAQ/docs/tree/main/specbatch/r886.md) -- Data Getter from MPI
    - [mpisink](https://github.com/FRIBDAQ/docs/tree/main/specbatch/r908.md) -- Send data to MPI getters.

- **List of Examples**
- 2-1. [Incorporating batch SpecTcl: Specifying the TCL Library on the command line:](https://github.com/FRIBDAQ/docs/tree/main/specbatch/c37.md#AEN57)
- 2-2. [Incorporating batch SpecTcl: adding the Tcl library to the `auto_path`](https://github.com/FRIBDAQ/docs/tree/main/specbatch/c37.md#AEN60)
- 2-3. [Using the **filesource** command](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x192.md#AEN214)
- 2-4. [Analyzing a run](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x192.md#AEN227)
- 2-5. [Obtaining the batch SpecTcl skeleton](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x230.md#AEN249)
- 2-6. [Including event processor headers](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x230.md#AEN268)
- 2-7. [Registering your event processing pipeline](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x230.md#AEN275)
- 2-8. [Setting the package name and version](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x230.md#AEN282)
- 2-9. [Initialization entry point](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x230.md#AEN297)
- 2-10. [Batch SpecTcl Makefile](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x230.md#AEN303)
- 2-11. [Smaple batch SpecTcl script.](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x342.md#AEN359)
- 2-12. [Reading a file with several spectra:](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x342.md#AEN388)
- 2-13. [Reading several multi segmented runs:](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x342.md#AEN394)
- 2-14. [Ordering run segments by segment number](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x342.md#AEN401)
- 3-1. [Running MPITcl](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x501.md#AEN506)
- 3-2. [Toy MPITcl application](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x501.md#AEN511)
- 4-1. [Package and definition loads](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x583.md#AEN588)
- 4-2. [Setting up sources and distirbutors](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x583.md#AEN593)
- 4-3. [Analyze the file in parallel:](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x583.md#AEN598)
- 4-4. [Getting and saving the results.](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x583.md#AEN602)
- 4-5. [Initiating spectrum data collection and waiting for all the workers to report.](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x583.md#AEN608)
- 4-6. [Receiving data from a worker:](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x583.md#AEN620)
- 4-7. [Exiting parallel SpecTcl](https://github.com/FRIBDAQ/docs/tree/main/specbatch/x583.md#AEN631)
- A-1. [Terminating an MPITcl application](https://github.com/FRIBDAQ/docs/tree/main/specbatch/r749.md#AEN850)

---

---

[← MPISpecTcl - Massively parallel SpecTcl.](https://github.com/FRIBDAQ/docs/tree/main/specbatch/c74.md) | [Home](https://github.com/FRIBDAQ/docs/tree/main/Home.md) | [analysissink →](https://github.com/FRIBDAQ/docs/tree/main/specbatch/r641.md)
