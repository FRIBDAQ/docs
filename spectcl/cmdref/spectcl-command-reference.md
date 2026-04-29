<a name="AEN1"></a># <a name="AEN2"></a>SpecTcl Command Reference.

### <a name="AEN4"></a>Ron Fox


---

**Table of Contents**1. [[c13]]I. [[r16]][[r18]] -- Apply gates to spectra and show which are applied.[[r108]] -- Connect SpecTcl to a data source[[r236]] -- Store spectrum channels in display share memory[[r300]] -- 1-d Spectrum fitting computation[[r465]] -- Apply a gamma gate as a fold[[r524]] -- Access spectrum channels[[r583]] -- Clear spectra[[r652]] -- Create projections of 2-d spectra[[r735]] -- Return spectrum statistics information[[r780]] -- Create list or modify characteristics treeparameters[[r1032]] -- List and manipulate tree variables[[r1196]] -- Create filtered data sets[[r1428]] -- Create, list, delete gates[[r1822]] -- Integrate regions of interest on spectra[[r1868]] -- Define, list and delete parameter definitions[[r2084]] -- Create, listm, delete pseudo parameters.[[r2207]] -- Read spectrum from file or pipe.[[r2347]] -- Select ringbuffer format[[r2384]] -- Obtain spectrum bulk contents[[r2445]] -- Get shared memory key.[[r2459]] -- Return the size of the spectrum shared memory region.[[r2473]] -- Create, list, delete, and trace changes to spectrum definitions.[[r2855]] -- Move spectrum storage out of shared display memory[[r2905]] -- Remove gate applications.[[r2935]] -- Return SpecTcl version[[r2962]] -- Write spectrum contents to file.[[r3039]] -- Start analyzing data[[r3070]] -- stop analyzing data[[r3097]] -- Execute a root macro file.[[r3125]] -- Write CERN ROOT Trees.[[r3172]] -- V5.1+ Manipulate the SpecTcl Analysis Pipeline[[r3327]] -- Dynamically setup decoding of event built data.[[r3394]] -- Test for remote-ness.[[r3408]] -- List Display Memory mirrors.[[r3436]] -- Create, maniuplate and query waveform objects

**List of Figures**1. [[r1428#AEN1526]]2. [[r1428#AEN1540]]

**List of Examples**1. [[r18#AEN64]]2. [[r18#AEN71]]3. [[r18#AEN81]]4. [[r18#AEN95]]1. [[r108#AEN203]]2. [[r108#AEN210]]3. [[r108#AEN219]]1. [[r236#AEN276]]2. [[r236#AEN280]]3. [[r236#AEN284]]1. [[r300#AEN456]]1. [[r524#AEN565]]2. [[r524#AEN568]]1. [[r583#AEN627]]2. [[r583#AEN630]]3. [[r583#AEN633]]4. [[r583#AEN636]]1. [[r780#AEN982]]2. [[r780#AEN991]]3. [[r780#AEN996]]4. [[r780#AEN1001]]5. [[r780#AEN1012]]1. [[r1032#AEN1143]]2. [[r1032#AEN1149]]3. [[r1032#AEN1155]]4. [[r1032#AEN1165]]5. [[r1032#AEN1177]]1. [[r1196#AEN1385]]2. [[r1196#AEN1396]]3. [[r1196#AEN1404]]1. [[r1428#AEN1792]]2. [[r1428#AEN1796]]3. [[r1428#AEN1800]]4. [[r1428#AEN1804]]1. [[r1868#AEN2061]]2. [[r1868#AEN2065]]1. [[r2084#AEN2169]]2. [[r2084#AEN2184]]3. [[r2084#AEN2188]]1. [[r2207#AEN2312]]2. [[r2207#AEN2318]]3. [[r2207#AEN2329]]1. [[r2347#AEN2371]]2. [[r2347#AEN2375]]1. [[r2473#AEN2743]]2. [[r2473#AEN2749]]3. [[r2473#AEN2755]]4. [[r2473#AEN2761]]5. [[r2473#AEN2767]]6. [[r2473#AEN2773]]7. [[r2473#AEN2779]]8. [[r2473#AEN2785]]9. [[r2473#AEN2791]]10. [[r2473#AEN2797]]11. [[r2473#AEN2803]]12. [[r2473#AEN2809]]13. [[r2473#AEN2815]]14. [[r2473#AEN2819]]1. [[r2962#AEN3014]]2. [[r2962#AEN3019]]

---

|  |  |  |
| --- | --- | --- |
|  |  | Next |
|  |  | Introduction |
