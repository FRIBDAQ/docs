[← The python spectcl package](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/c81.md) | [Home](https://github.com/FRIBDAQ/docs/tree/main/Home.md) | [listparams →](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/r109.md)

---

<a name="AEN1"></a># <a name="AEN2"></a>SpecTcl Python package

### <a name="AEN4"></a>Ron Fox


---

- **Table of Contents**
- 1. [Introduction](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/c13.md)
- 2. [The **python** command.](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/c23.md)
  - [python](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/r28.md) -- Runs python scripts in SpecTcl
- 3. [The python spectcl package](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/c81.md)
  - 3.1. [spectcl package level methods.](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/c81.md#AEN89)
    - [tcl](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/r91.md) -- Run a Tcl script from Python.
    - [listparams](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/r109.md) -- Creates a listing of defined parameters.
    - [listspectra](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/r130.md) -- Create a list of defined spectrum names.
    - [listvars](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/r143.md) -- Get a list of tree variables.
    - [listgates](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/r156.md) -- Create a list of gate names.
    - [attach](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/r169.md) -- Attach SpecTcl to a data source.
    - [start](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/r260.md) -- Start analyzing data.
    - [stop](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/r279.md) -- Stop data analysis
  - 3.2. [The spectcl.parameter type](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/x294.md)
    - [parameter](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/r298.md) -- Wrap SpecTcl parameter/treeparameters
  - 3.3. [The spectcl.spectrum type](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/x408.md)
    - [spectrum](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/r416.md) -- Wrap SpecTcl Spectrum objects.
  - 3.4. [The spectcl.variable type](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/x712.md)
    - [variable](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/r716.md) -- Wrapper for SpecTcl tree variable objects.
  - 3.5. [The spectcl.gates type](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/x840.md)
    - [gate](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/r848.md) -- Wraps a gate via its gate container.

- **List of Examples**
- 2-1. [Running a script file](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/r28.md#AEN59)
- 2-2. [Running an immediate script](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/r28.md#AEN65)
- 2-3. [Tcl variable substitution](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/r28.md#AEN74)
- 3-1. [Listing all parameters to tkcon](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/r109.md#AEN124)
- 3-1. [Attaching a file data source](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/r169.md#AEN232)
- 3-2. [Taking data from an NSCLDAQ ringbuffer](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/r169.md#AEN237)
- 3-3. [Reading data from a gzipped event file](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/r169.md#AEN254)

---

---

[← The python spectcl package](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/c81.md) | [Home](https://github.com/FRIBDAQ/docs/tree/main/Home.md) | [listparams →](https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/r109.md)
