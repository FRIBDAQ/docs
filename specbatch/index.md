<a name="AEN1"></a># <a name="AEN2"></a>Batch SpecTcl (5.2 and later)

### <a name="AEN4"></a>Ron Fox


---

- **Table of Contents**
- 1. [[Introduction|c13]]
- 2. [[Serial batch SpectTcl|c37]]
  - 2.1. [[Incorporating batch SpecTcl in to a Tcl interpreter|c37#AEN52]]
  - 2.2. [[Commands supported by batch SpecTcl|x66]]
  - 2.3. [[How Batch SpeTcl analyzes data|x192]]
  - 2.4. [[Creating a loadable package for the event analysis pipeline|x230]]
  - 2.5. [[A simple analysis script.|x342]]
- 3. [[MPITcl - an enhanced Tcl interpreter|c406]]
  - 3.1. [[MPI Concepts|c406#AEN422]]
  - 3.2. [[How MPI Concepts map to MPITcl|x431]]
  - 3.3. [[The mpi::mpi command ensemble.|x447]]
  - 3.4. [[Running MPITcl (NSCL/FRIB specific)|x501]]
- 4. [[MPISpecTcl - Massively parallel SpecTcl.|c549]]
  - 4.1. [[The mpispectcl package|c549#AEN562]]
  - 4.2. [[Parallel models for SpecTcl|x570]]
  - 4.3. [[Serial reader parallel worker example.|x583]]
- A. [[Reference (man) pages|a635]]
  - A.1. [[Batch SpecTcl|a635#AEN638]]
    - [[analysissink|r641]] -- Establish a data distributor to the anlaysis pipeline
    - [[analyze|r656]] -- Begin analysis.
    - [[filesource|r672]] -- Establish a data getter from a file.
    - [[CDataGetter|r690]] -- Base class for data getters.
    - [[CDataDistributor|r732]] -- Data Distribution base class.
  - A.2. [[MPITcl|x746]]
    - [[mpi::mpi|r749]] -- Command ensemble for MPI under tcl.
    - [[MPITcl binary data.|r853]] -- Receiving binary data in compiled MPITcl extensions
  - A.3. [[MPI SpecTcl|x882]]
    - [[mpisource|r886]] -- Data Getter from MPI
    - [[mpisink|r908]] -- Send data to MPI getters.

- **List of Examples**
- 2-1. [[Incorporating batch SpecTcl: Specifying the TCL Library on the command line:|c37#AEN57]]
- 2-2. [[Incorporating batch SpecTcl: adding the Tcl library to the `auto_path`|c37#AEN60]]
- 2-3. [[Using the **filesource** command|x192#AEN214]]
- 2-4. [[Analyzing a run|x192#AEN227]]
- 2-5. [[Obtaining the batch SpecTcl skeleton|x230#AEN249]]
- 2-6. [[Including event processor headers|x230#AEN268]]
- 2-7. [[Registering your event processing pipeline|x230#AEN275]]
- 2-8. [[Setting the package name and version|x230#AEN282]]
- 2-9. [[Initialization entry point|x230#AEN297]]
- 2-10. [[Batch SpecTcl Makefile|x230#AEN303]]
- 2-11. [[Smaple batch SpecTcl script.|x342#AEN359]]
- 2-12. [[Reading a file with several spectra:|x342#AEN388]]
- 2-13. [[Reading several multi segmented runs:|x342#AEN394]]
- 2-14. [[Ordering run segments by segment number|x342#AEN401]]
- 3-1. [[Running MPITcl|x501#AEN506]]
- 3-2. [[Toy MPITcl application|x501#AEN511]]
- 4-1. [[Package and definition loads|x583#AEN588]]
- 4-2. [[Setting up sources and distirbutors|x583#AEN593]]
- 4-3. [[Analyze the file in parallel:|x583#AEN598]]
- 4-4. [[Getting and saving the results.|x583#AEN602]]
- 4-5. [[Initiating spectrum data collection and waiting for all the workers to report.|x583#AEN608]]
- 4-6. [[Receiving data from a worker:|x583#AEN620]]
- 4-7. [[Exiting parallel SpecTcl|x583#AEN631]]
- A-1. [[Terminating an MPITcl application|r749#AEN850]]

---

|  |  |  |
| --- | --- | --- |
|  |  | Next |
|  |  | Introduction |
