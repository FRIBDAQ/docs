|  |  |  |
| --- | --- | --- |
| mpiSpecTcl. |
| Prev |  |  |


---

# <a name="AEN2325"></a>Appendix D. XXUSB SpecTcl with MPI parallelism

Only VMUSBSpecTcl has been made to support MPI parallel
            operation.  If CCUSBSpecTcl is run under **mpirun**
            it will output an error message and exit immediately with an error status.

VMUSB SpecTcls require that configuration support packages
            and configuration scripts be loaded into all of the
            processes of MPI SpecTcl.   This ensures that all parameters,
            spectra and decode tables get loaded whereever they are needed.

If you are taking the skeletons for these versions of
            SpecTcl from 7.0 or later everything should just work.
            If, on the other hand you are moving to SpecTcl 7.0 from 
            an earlier version, this appendix describes what you need to 
            do to make the transition:



1. Ensure the MPI Tcl package is loaded in all ranks.
2. Edit SpecTclRC.tcl so that
                   the configuration part of that script is executed
                    in all ranks.

Loading the MPI Tcl package in all ranks is accomplised by 
            adding the following lines to your SpecTclInit.tcl

<a name="AEN2339"></a>```
load [file join $SpecTclHome lib/libMPITclPackage.so]
package require mpi
        
```

Be sure to put these lines in SpecTclInit.tcl
*not* in 
            SpecTclRC.tcl.

This has been added to the SpecTclInit.tcl that
            is now in the VMUSBSkel directory of the SpecTcl
            insallation.

# <a name="AEN2348"></a>D.1. VMUSBSpecTcl

You must make sure that the section of VMUSBSpecTcl's 
                SpecTclRC.tcl that reads the configuration
                support and your configuration script is executed in all ranks:

<a name="AEN2352"></a>**Example D-1. VMUSB configuration**

```
 mpi::send all {
	set daqconfig [file join daqconfig.tcl]; # default config file.
	lappend auto_path [file join $SpecTclHome TclLibs]
	package require vmusbsetup

	vmusbConfig $daqconfig
}               
```

Note how the entire block of code that configures SpecTcl's
                VMUSB support and its processing of the configuration file
                are wrapped in a **mpi::send all ...**.

The SpecTclRC.tcl in the 
                VMUSBSkel directory of the SpecTcl installation
                is now like that.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home |  |
| mpi::send |  |  |
