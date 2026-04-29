<a name="AEN1"></a># <a name="AEN2"></a>SpecTcl Command Reference.

### <a name="AEN4"></a>Ron Fox


---

- **Table of Contents**
- 1. [[Introduction|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/c13.md]]
- I. [[SpecTcl Commands|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r16.md]]
  - [[apply|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r18.md]] -- Show which gates are applied to which spectra
  - [[attach|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r102.md]] -- Connect SpecTcl to a data source
  - [[sbind|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r230.md]] -- Store spectrum channels in display share memory
  - [[fit|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r294.md]] -- 1-d Spectrum fitting computation
  - [[fold|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r459.md]] -- Apply a gamma gate as a fold
  - [[channel|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r518.md]] -- Access spectrum channels
  - [[clear|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r577.md]] -- Clear spectra
  - [[project|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r646.md]] -- Create projections of 2-d spectra
  - [[specstats|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r729.md]] -- Return spectrum statistics information
  - [[treeparameter|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r774.md]] -- Create list or modify characteristics treeparameters
  - [[treevariable|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r1026.md]] -- List and manipulate tree variables
  - [[filter|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r1190.md]] -- Create filtered data sets
  - [[gate|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r1422.md]] -- Create, list, delete gates
  - [[integrate|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r1816.md]] -- Integrate regions of interest on spectra
  - [[parameter|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r1862.md]] -- Define, list and delete parameter definitions
  - [[pseudo|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2051.md]] -- Create, listm, delete pseudo parameters.
  - [[sread|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2174.md]] -- Read spectrum from file or pipe.
  - [[ringformat|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2285.md]] -- Select ringbuffer format
  - [[scontents|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2322.md]] -- Obtain spectrum bulk contents
  - [[shmemkey|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2383.md]] -- Get shared memory key.
  - [[shmemsize|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2397.md]] -- Return the size of the spectrum shared memory region.
  - [[spectrum|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2411.md]] -- Create, list, delete, and trace changes to spectrum definitions.
  - [[unbind|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2793.md]] -- Move spectrum storage out of shared display memory
  - [[ungate|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2847.md]] -- Remove gate applications.
  - [[version|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2877.md]] -- Return SpecTcl version
  - [[sread|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2904.md]] -- Write spectrum contents to file.
  - [[start|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2974.md]] -- Start analyzing data
  - [[start|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r3005.md]] -- stop analyzing data
  - [[rootexec|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r3032.md]] -- Execute a root macro file.
  - [[roottree|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r3059.md]] -- Write CERN ROOT Trees.
  - [[pman|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r3102.md]] -- V5.1+ Manipulate the SpecTcl Analysis Pipeline
  - [[evbunpack|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r3247.md]] -- Dynamically setup decoding of event built data.

- **List of Figures**
- 1. [[A band draw with backtracking|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r1422.md#AEN1520]]
- 2. [[Contour interior|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r1422.md#AEN1534]]

- **List of Examples**
- 1. [[Applying a gate to a single spectrum|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r18.md#AEN58]]
- 2. [[Applying a gate to several spectra|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r18.md#AEN65]]
- 3. [[Listing gates applied to all spectra|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r18.md#AEN75]]
- 4. [[Using a filter to list gate applications|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r18.md#AEN89]]
- 1. [[Attaching to a data file for nscldaq-11:|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r102.md#AEN197]]
- 2. [[Attaching to the online system via a pipe data source|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r102.md#AEN204]]
- 3. [[Attaching to a compressed datafile:|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r102.md#AEN213]]
- 1. [[Binding all spectra to display memory|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r230.md#AEN270]]
- 2. [[Binding a list of spectra to the displayer|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r230.md#AEN274]]
- 3. [[Listing the bindings of spectra that match a pattern|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r230.md#AEN278]]
- 1. [[Using the proc subcommand|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r294.md#AEN450]]
- 1. [[Getting the value of a channel in a 1-d spectrum|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r518.md#AEN559]]
- 2. [[Clearing a spectrum using **channel**|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r518.md#AEN562]]
- 1. [[Clearing all spectra|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r577.md#AEN621]]
- 2. [[Clearing spectra given their names|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r577.md#AEN624]]
- 3. [[Clearing spectra given their ids:|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r577.md#AEN627]]
- 4. [[Clearing spectra whose names match a glob pattern r*|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r577.md#AEN630]]
- 1. [[Creating a new tree parameter|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r774.md#AEN976]]
- 2. [[Listing all tree parameters with sample output|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r774.md#AEN985]]
- 3. [[Listing only some parameters (using a pattern)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r774.md#AEN990]]
- 4. [[The treeparameter -check command|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r774.md#AEN995]]
- 5. [[Unsetting the modified flag:|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r774.md#AEN1006]]
- 1. [[Listing all variables:|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r1026.md#AEN1137]]
- 2. [[Using a glob pattern; listing variables thaty start with vars.w|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r1026.md#AEN1143]]
- 3. [[Modifying value and units of a tree variable|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r1026.md#AEN1149]]
- 4. [[Changing only the value of a tree parameter|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r1026.md#AEN1159]]
- 5. [[Modifying only the units of a tree variable|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r1026.md#AEN1171]]
- 1. [[Creating a filter|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r1190.md#AEN1379]]
- 2. [[Setting filter filenames|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r1190.md#AEN1390]]
- 3. [[Enabling filters|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r1190.md#AEN1398]]
- 1. [[Creating a slice gate|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r1422.md#AEN1786]]
- 2. [[Listing all gates|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r1422.md#AEN1790]]
- 3. [[Deleting a gate|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r1422.md#AEN1794]]
- 4. [[Establishing a trace|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r1422.md#AEN1798]]
- 1. [[Creating a 12 bit 'integer' parameter|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r1862.md#AEN2028]]
- 2. [[Creating a real valued parameter with units in mm|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r1862.md#AEN2032]]
- 1. [[Defining a simple psuedo|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2051.md#AEN2136]]
- 2. [[Pseudo illustrating quoting:|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2051.md#AEN2151]]
- 3. [[listing pseudos|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2051.md#AEN2155]]
- 1. [[Reading a spectrum in from file|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2174.md#AEN2251]]
- 2. [[Reading several spectra from one file|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2174.md#AEN2257]]
- 3. [[Reading from a pipeline:|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2174.md#AEN2267]]
- 1. [[NSCLDAQ version 10 data:|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2285.md#AEN2309]]
- 2. [[NSDCLDAQ version 11 data|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2285.md#AEN2313]]
- 1. [[Creating a 1-d spectrum|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2411.md#AEN2681]]
- 2. [[Creating a 2-d spectrum|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2411.md#AEN2687]]
- 3. [[Creating a g1 spectrum|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2411.md#AEN2693]]
- 4. [[Creating a g2 spectrum|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2411.md#AEN2699]]
- 5. [[Creating a summary spectrum|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2411.md#AEN2705]]
- 6. [[Creating a bitmask spectrum|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2411.md#AEN2711]]
- 7. [[Making a strip chart spectrum|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2411.md#AEN2717]]
- 8. [[Creating an m2 (multiple 2d spectrum)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2411.md#AEN2723]]
- 9. [[Creating a gd (gamma deluxe) spectrum|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2411.md#AEN2729]]
- 10. [[Creating a gs (gamma summary) spectrum|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2411.md#AEN2735]]
- 11. [[Listing all spectra|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2411.md#AEN2741]]
- 12. [[Listing only spectra with matching names|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2411.md#AEN2747]]
- 13. [[Deleting a spectrum|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2411.md#AEN2753]]
- 14. [[Spectrum traces:|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2411.md#AEN2757]]
- 1. [[Writing spectra to file by filename|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2904.md#AEN2949]]
- 2. [[Writing to a file descriptor|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/cmdref/r2904.md#AEN2954]]

---

|  |  |  |
| --- | --- | --- |
|  |  | Next |
|  |  | Introduction |
