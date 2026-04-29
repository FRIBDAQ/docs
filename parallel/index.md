<a name="AEN1"></a># <a name="AEN2"></a>mpiSpecTcl.

### <a name="AEN4"></a>Ron Fox


---

**Table of Contents**1. [[c13]]1.1. [[c13#AEN27]]1.2. [[x34]]1.3. [[x48]]1.4. [[x56]]1.5. [[x80]]2. [[c103]]2.1. [[c103#AEN120]]2.2. [[x216]]2.3. [[x266]]3. [[c362]]3.1. [[c362#AEN390]]3.2. [[x417]]3.2.1. [[x417#AEN431]]3.2.2. [[x417#AEN447]]3.2.3. [[x417#AEN453]]3.3. [[x462]]3.3.1. [[x462#AEN517]]3.3.2. [[x462#sec.ringpump]]3.3.3. [[x462#AEN571]]3.3.4. [[x462#AEN610]]3.3.5. [[x462#AEN624]]3.4. [[x641]]3.4.1. [[x641#AEN678]]3.4.2. [[x641#AEN712]]3.4.3. [[x641#AEN732]]3.5. [[x746]]A. [[a773]]A.1. [[a773#AEN776]][[r779]] -- Describe MPI specific definitions in Globals.h[[r846]] -- Utility definitions in TclPump.hA.2. [[x887]][[r893]] -- Jacket a command that runs in all ranks[[r948]] -- Jacket a command that runs in other ranks[[r998]] -- Wrap a packaged command that will execute in all processes[[r1052]] -- Jacket packagted commands to run in all but he root.B. [[a1102]][[r1108]] -- Apply a gate to one or more spectra[[r1145]] -- Attach a data source to SpecTcl[[r1188]] -- Describe mpiSpecTcl implementation of the channel command.[[r1222]] -- MPI SpecTcl clear command[[r1265]] -- mpiSpecTcl implementation of evbunpack[[r1298]] -- MPISpectcl Implementation of the filter command[[r1363]] -- Operation of fit command in mpiSpecTcl[[r1406]] -- THe fold command on mpiSpecTcl[[r1439]] -- Behavior of the gate command in mpiSpecTcl[[r1492]] -- Integrate an area of interest[[r1515]] -- List sthe mirrors being run[[r1534]] -- Manipulate parametes.[[r1585]] -- Manipulate data analysis piplines[[r1656]] -- Create projection spectra[[r1684]] -- Create and manipulate pseudo parameters[[r1717]] -- Allow scripts to know if they are operating remot of SpecTcl[[r1734]] -- Set the ring buffer fallback format version[[r1752]] -- Bind spectra into the shared display memory[[r1791]] -- Provide display shared memory identification[[r1809]] -- Get the size of the spectrum pool of display shared memory[[r1827]] -- Fetch spectrum over/underlow statistics[[r1847]] -- Provide the SpecTcl version[[r1864]] -- Create and manipulate spectrum definitions[[r1933]] -- Read spectra from file[[r1963]] -- start analysis from the current data source[[r1977]] -- Stop analyzing data from the data source[[r1993]] -- Write spectra to file[[r2016]] -- Manipulate the metadatak of tree parameters[[r2121]] -- Manipulate Tree variables[[r2169]] -- Unbind spectra from display shared memory[[r2198]] -- Remove gate conditions from spectraC. [[a2217]][[r2273]] -- Allow rank 0 to execute scripts in other ranks.
                D. [[a2325]]D.1. [[a2325#AEN2348]]

**List of Examples**1-1. [[x34#ex.version]]1-2. [[x56#AEN62]]1-3. [[x80#AEN92]]2-1. [[c103#AEN141]]2-2. [[c103#AEN192]]2-3. [[c103#AEN208]]2-4. [[x216#AEN263]]2-5. [[x266#AEN327]]2-6. [[x266#AEN340]]2-7. [[x266#AEN352]]3-1. [[x417#AEN457]]3-2. [[x462#AEN473]]C-1. [[a2217#AEN2223]]C-1. [[r2273#AEN2312]]C-2. [[r2273#AEN2317]]C-3. [[r2273#AEN2320]]D-1. [[a2325#AEN2352]]

---

|  |  |  |
| --- | --- | --- |
|  |  | Next |
|  |  | Quick Start |
