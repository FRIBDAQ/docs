The FRIBDAQ (previously known as NSCLDAQ) software described in this documentation is licensed for
     use by the MSU Board of trustees under the GNU Public Licesne

     see [[ http://www.gnu.org/licenses/gpl.txt]]
     for terms and conditions


Other, open source, software is re-distributed with permission of the
    Copyright owners.  Refer to the licensing information included with the
    source distributions for individual licensing terms.


# DAQ presentations


- [[nscldaqtofribdaq.pdf]]


# Containerized FRIBDAQ


Beginning with the deployment of Debian-10 (buster) at the NSCL/FRIB,
    FRIBDAQ software is run within singularity containers.  These containers
    provide a zero overhead  stable environment from which the software can be
    run that is 
    insulated from changes to the host system.  Furtheremore containers allow
    us to maintain support for prior distributions of Debian even past their
    expiration date



- [[container-instructions.pdf]] for
        using the 
  	container environments we created at the FRIB.
- Containerized environments also provide a simplified installation
        of FRIBDAQ software for external
        users.[[DAQFromContainers.pdf]] describes how to
  	install a containerized FRIBDAQ.
- [[extending-containers.pdf]] for
  	extending the containers we provide.


# What is FRIBDAQ?


FRIBDAQ is a software suite that provides a flexible and extensible
    framework for handling the data flow produced by nuclear physics
    experiments.  It aims to solve the top-level problem of managing the data
    stream by breaking it down into smaller problems solved by smaller
    applications. It therefore is a collection of tools that can be assembled
    into more complicated applications. This approach enables FRIBDAQ to be a
    modular system capable of tackling a wide range of experimental setups, from
    small calibration setups to merging multiple independent data acquisitions
    into unified systems.


FRIBDAQ is a winner of the Sourceforge community choice award


As you can imagine, FRIBDAQ is a large package with many utilities. Indeed 
     a lot of time has been spent documenting its capabilities. For more 
     details, please continue reading the [[nscldaq-11.0/index]] of the FRIBDAQ 11.0 comprehensive documentation. That should get 
     your feet wet.


- [[nscldaq-11.3/index]]
- [[cookbook/index]]
- [[daqformat/index]]


# What is SpecTcl?


SpecTcl is for analysis what FRIBDAQ is for dataflow. SpecTcl is a C++ 
      framework that allows experimenters to write custom analysis software that 
      seemlessly integrates with a histogramming engine and viewer.  SpecTcl
      enables the quick creation of histograms from the data and the ability to create
      1d and 2d gates and apply them to histograms on the fly.

SpecTcl is a winner of the SourceForge community choice award.


- [[spectcl-5.0/UserGuide/index]](Added June 13, 2017)
- [[spectcl/cmdref/index]] (Updated October 21, 2025)
- [[spectcl/pgmguide/index]] (Updated October 21, 2025)
- [[spectcl/pgmref/index]] (Updated October 21, 2025)
- [[spectcl-5.0/DDAS/index]]
- [[specbatch/index]]
- [[spectcl/restdocs/index]] (Updated October 21, 2025)
- [[parallel/index]]
- [[qtpy/index]]
- [[genx/index]]
- [[spectcl-5.0/python/index]]
- [[rootxamine/index]]
- [[spectcldb/index]]
  	    (SpecTcl 5.3 and later), provides an Sqlite3 based store for
  	    SpecTcl objects and pre-processed event data.
- [[vmusbspectcl/index]]
- [[mvlcspectcl/index]]
- SpecTcl Plugin documentation


# FRIB Analysis Pipeline


The FRIB Analysis Pipeline models analysis of data from experiments
	 as a pipeline of transformations from raw data to increasingly
	 physically meaningful parameters.  It provides parallel tools
	 for stages of that pipeline.

Documentation for the current version of this software is available
	 at [[apipeline/index]]
	 pages.   Installation of versions of this software is available
	 within the container filesystems from Buster on at
	  /usr/opt/frib-analysis/.


# What is DDAS?


The Digital Data Acquisition System (DDAS) is a lab-supported data acquisition
      system built around the XIA Pixie-16 Digitizer running the general-purpose firmware
      developed by XIA for the NSCL. The system is very flexible and is capable
      of reading out a wide range of detectors. DDAS provides tools for configuring the
      the digitizers, reading them out, and analyzing the resulting data. All of this
      is built on top of FRIBDAQ frameworks and is therefore completely compatible with
      FRIBDAQ.


- [[ddas-12.1-001/index]]
  Note that this guide is specific to FRIBDAQ 12.0 and later; for legacy DDAS, see the [[ddas-1.1/index]]
- [[ddasformat-1.1-001/index]]
- [[ddastoys-6.2-000/index]]
- [[pixie16/Pixie16_UserManual.pdf]]


# FRIBDAQ Support for GET electronics


The GET (Generalized Electronics for TPCs) is a high density electronics
   package that provides 100Mhz digitized signals.  Support for a single CoBo
   is now available for SPDAQ systems that are configured to interface with
   GET Micro-TCA crates. See:


### [[../get/index]]


# Rustogrammer a new histogramer


Rustogrammer is a new histograming package written in rust and portable
      to Windows.  With the Cutiepie displayer having been ported to windows
      and the availability of a portable PyQt front end that is similar to the
      Tree GUI available in SpecTcl, this package brings analysis power similar
      to SpecTcl to the desktop.

      See
      [[rustogramer/index]]
