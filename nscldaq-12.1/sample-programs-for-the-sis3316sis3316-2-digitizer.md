|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN9201"></a>Chapter 21. Sample programs for the SIS3316/SIS3316-2 digitizer.

FRIBDAQ includes the SIS3316 sample programs ported to 
        run under the VMUSB VME controller.  Refer to the SIS3316
        documentation for information about these programs and what they do.

Programs are installed in 
        $DAQROOT/sis3316 rather than $DAQBIN in order to
        keep them separate from standard FRIBDAQ software.  Some programs
        can take configuration files that define digitizer parameters.
        Those get installed in 
        $DAQSHARE/sis3316_configs.

The root_gui program depends on images
        for e.g. the program icon.  These are installed in
        $DAQSHARE/sis_images.

In addition to the SIS examples a program named
        inventory is installed.  This looks at all possible
        base addresses for SIS3316 modules and reports which bases have such modules
        as well as some information about those modules.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Overview of Basic Operation | Up | commands |
