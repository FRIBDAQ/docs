[← Introduction](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/c13.md) | [Home](https://github.com/FRIBDAQ/docs/tree/main/Home.md) | [treevariable →](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r1032.md)

---

<a name="AEN1"></a># <a name="AEN2"></a>SpecTcl Command Reference.

### <a name="AEN4"></a>Ron Fox


---

- **Table of Contents**
- 1. [Introduction](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/c13.md)
- I. [SpecTcl Commands](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r16.md)
  - [applygate](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r18.md) -- Apply gates to spectra and show which are applied.
  - [attach](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r108.md) -- Connect SpecTcl to a data source
  - [sbind](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r236.md) -- Store spectrum channels in display share memory
  - [fit](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r300.md) -- 1-d Spectrum fitting computation
  - [fold](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r465.md) -- Apply a gamma gate as a fold
  - [channel](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r524.md) -- Access spectrum channels
  - [clear](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r583.md) -- Clear spectra
  - [project](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r652.md) -- Create projections of 2-d spectra
  - [specstats](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r735.md) -- Return spectrum statistics information
  - [treeparameter](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r780.md) -- Create list or modify characteristics treeparameters
  - [treevariable](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r1032.md) -- List and manipulate tree variables
  - [filter](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r1196.md) -- Create filtered data sets
  - [gate](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r1428.md) -- Create, list, delete gates
  - [integrate](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r1822.md) -- Integrate regions of interest on spectra
  - [parameter](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r1868.md) -- Define, list and delete parameter definitions
  - [pseudo](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2084.md) -- Create, listm, delete pseudo parameters.
  - [sread](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2207.md) -- Read spectrum from file or pipe.
  - [ringformat](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2347.md) -- Select ringbuffer format
  - [scontents](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2384.md) -- Obtain spectrum bulk contents
  - [shmemkey](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2445.md) -- Get shared memory key.
  - [shmemsize](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2459.md) -- Return the size of the spectrum shared memory region.
  - [spectrum](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2473.md) -- Create, list, delete, and trace changes to spectrum definitions.
  - [unbind](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2855.md) -- Move spectrum storage out of shared display memory
  - [ungate](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2905.md) -- Remove gate applications.
  - [version](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2935.md) -- Return SpecTcl version
  - [swrite](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2962.md) -- Write spectrum contents to file.
  - [start](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r3039.md) -- Start analyzing data
  - [start](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r3070.md) -- stop analyzing data
  - [rootexec](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r3097.md) -- Execute a root macro file.
  - [roottree](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r3125.md) -- Write CERN ROOT Trees.
  - [pman](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r3172.md) -- V5.1+ Manipulate the SpecTcl Analysis Pipeline
  - [evbunpack](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r3327.md) -- Dynamically setup decoding of event built data.
  - [isRemote](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r3394.md) -- Test for remote-ness.
  - [mirror](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r3408.md) -- List Display Memory mirrors.
  - [waveform](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r3436.md) -- Create, maniuplate and query waveform objects

- **List of Figures**
- 1. [A band draw with backtracking](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r1428.md#AEN1526)
- 2. [Contour interior](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r1428.md#AEN1540)

- **List of Examples**
- 1. [Applying a gate to a single spectrum](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r18.md#AEN64)
- 2. [Applying a gate to several spectra](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r18.md#AEN71)
- 3. [Listing gates applied to all spectra](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r18.md#AEN81)
- 4. [Using a filter to list gate applications](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r18.md#AEN95)
- 1. [Attaching to a data file for nscldaq-11:](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r108.md#AEN203)
- 2. [Attaching to the online system via a pipe data source](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r108.md#AEN210)
- 3. [Attaching to a compressed datafile:](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r108.md#AEN219)
- 1. [Binding all spectra to display memory](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r236.md#AEN276)
- 2. [Binding a list of spectra to the displayer](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r236.md#AEN280)
- 3. [Listing the bindings of spectra that match a pattern](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r236.md#AEN284)
- 1. [Using the proc subcommand](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r300.md#AEN456)
- 1. [Getting the value of a channel in a 1-d spectrum](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r524.md#AEN565)
- 2. [Clearing a spectrum using **channel**](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r524.md#AEN568)
- 1. [Clearing all spectra](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r583.md#AEN627)
- 2. [Clearing spectra given their names](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r583.md#AEN630)
- 3. [Clearing spectra given their ids:](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r583.md#AEN633)
- 4. [Clearing spectra whose names match a glob pattern r*](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r583.md#AEN636)
- 1. [Creating a new tree parameter](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r780.md#AEN982)
- 2. [Listing all tree parameters with sample output](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r780.md#AEN991)
- 3. [Listing only some parameters (using a pattern)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r780.md#AEN996)
- 4. [The treeparameter -check command](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r780.md#AEN1001)
- 5. [Unsetting the modified flag:](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r780.md#AEN1012)
- 1. [Listing all variables:](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r1032.md#AEN1143)
- 2. [Using a glob pattern; listing variables thaty start with vars.w](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r1032.md#AEN1149)
- 3. [Modifying value and units of a tree variable](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r1032.md#AEN1155)
- 4. [Changing only the value of a tree parameter](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r1032.md#AEN1165)
- 5. [Modifying only the units of a tree variable](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r1032.md#AEN1177)
- 1. [Creating a filter](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r1196.md#AEN1385)
- 2. [Setting filter filenames](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r1196.md#AEN1396)
- 3. [Enabling filters](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r1196.md#AEN1404)
- 1. [Creating a slice gate](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r1428.md#AEN1792)
- 2. [Listing all gates](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r1428.md#AEN1796)
- 3. [Deleting a gate](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r1428.md#AEN1800)
- 4. [Establishing a trace](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r1428.md#AEN1804)
- 1. [Creating a 12 bit 'integer' parameter](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r1868.md#AEN2061)
- 2. [Creating a real valued parameter with units in mm](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r1868.md#AEN2065)
- 1. [Defining a simple psuedo](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2084.md#AEN2169)
- 2. [Pseudo illustrating quoting:](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2084.md#AEN2184)
- 3. [listing pseudos](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2084.md#AEN2188)
- 1. [Reading a spectrum in from file](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2207.md#AEN2312)
- 2. [Reading several spectra from one file](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2207.md#AEN2318)
- 3. [Reading from a pipeline:](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2207.md#AEN2329)
- 1. [NSCLDAQ version 10 data:](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2347.md#AEN2371)
- 2. [NSDCLDAQ version 11 data](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2347.md#AEN2375)
- 1. [Creating a 1-d spectrum](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2473.md#AEN2743)
- 2. [Creating a 2-d spectrum](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2473.md#AEN2749)
- 3. [Creating a g1 spectrum](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2473.md#AEN2755)
- 4. [Creating a g2 spectrum](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2473.md#AEN2761)
- 5. [Creating a summary spectrum](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2473.md#AEN2767)
- 6. [Creating a bitmask spectrum](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2473.md#AEN2773)
- 7. [Making a strip chart spectrum](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2473.md#AEN2779)
- 8. [Creating an m2 (multiple 2d spectrum)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2473.md#AEN2785)
- 9. [Creating a gd (gamma deluxe) spectrum](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2473.md#AEN2791)
- 10. [Creating a gs (gamma summary) spectrum](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2473.md#AEN2797)
- 11. [Listing all spectra](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2473.md#AEN2803)
- 12. [Listing only spectra with matching names](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2473.md#AEN2809)
- 13. [Deleting a spectrum](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2473.md#AEN2815)
- 14. [Spectrum traces:](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2473.md#AEN2819)
- 1. [Writing spectra to file by filename](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2962.md#AEN3014)
- 2. [Writing to a file descriptor](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r2962.md#AEN3019)

---

---

[← Introduction](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/c13.md) | [Home](https://github.com/FRIBDAQ/docs/tree/main/Home.md) | [treevariable →](https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/r1032.md)
