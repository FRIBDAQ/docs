The FRIBDAQ (previously known as NSCLDAQ) software described in this documentation is licensed for
     use by the MSU Board of trustees under the GNU Public Licesne

     see [[http://www.gnu.org/licenses/gpl.txt|https://github.com/FRIBDAQ/docs/tree/main/ http://www.gnu.org/licenses/gpl.txt.md]]
     for terms and conditions


Other, open source, software is re-distributed with permission of the
    Copyright owners.  Refer to the licensing information included with the
    source distributions for individual licensing terms.


# DAQ presentations


- [[Research Seminar 01/12/23|https://github.com/FRIBDAQ/docs/tree/main/nscldaqtofribdaq.pdf.md]]


# Containerized FRIBDAQ


Beginning with the deployment of Debian-10 (buster) at the NSCL/FRIB,
    FRIBDAQ software is run within singularity containers.  These containers
    provide a zero overhead  stable environment from which the software can be
    run that is 
    insulated from changes to the host system.  Furtheremore containers allow
    us to maintain support for prior distributions of Debian even past their
    expiration date



- [[Here are instructions|https://github.com/FRIBDAQ/docs/tree/main/container-instructions.pdf.md]] for
        using the 
  	container environments we created at the FRIB.
- Containerized environments also provide a simplified installation
        of FRIBDAQ software for external
        users.[[This document|https://github.com/FRIBDAQ/docs/tree/main/DAQFromContainers.pdf.md]] describes how to
  	install a containerized FRIBDAQ.
- [[Here are instructions|https://github.com/FRIBDAQ/docs/tree/main/extending-containers.pdf.md]] for
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
     details, please continue reading the [[user's 
     guide|https://github.com/FRIBDAQ/docs/tree/main/nscldaq-11.0/index.md]] of the FRIBDAQ 11.0 comprehensive documentation. That should get 
     your feet wet.


- [[## Proceed to User's
  	      Guide|https://github.com/FRIBDAQ/docs/tree/main/nscldaq-11.3/index.md]]
- [[## FRIBDAQ Cookbook recipes|https://github.com/FRIBDAQ/docs/tree/main/cookbook/index.md]]
- [[## Library to decode FRIBDAQ data from several versions|https://github.com/FRIBDAQ/docs/tree/main/daqformat/index.md]]


# What is SpecTcl?


SpecTcl is for analysis what FRIBDAQ is for dataflow. SpecTcl is a C++ 
      framework that allows experimenters to write custom analysis software that 
      seemlessly integrates with a histogramming engine and viewer.  SpecTcl
      enables the quick creation of histograms from the data and the ability to create
      1d and 2d gates and apply them to histograms on the fly.

SpecTcl is a winner of the SourceForge community choice award.


- [[User guide for
  	      5.0|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/UserGuide/index.md]](Added June 13, 2017)
- [[SpecTcl command
  	      reference|https://github.com/FRIBDAQ/docs/tree/main/spectcl/cmdref/index.md]] (Updated October 21, 2025)
- [[Programming guide for
  	      7.0|https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmguide/index.md]] (Updated October 21, 2025)
- [[Programming reference for
  	7.0|https://github.com/FRIBDAQ/docs/tree/main/spectcl/pgmref/index.md]] (Updated October 21, 2025)
- [[SpecTcl tools for DDAS
  	      (5.0-10 and later)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/DDAS/index.md]]
- [[SpecTcl Batch and parallel SpecTcl
  	    (5.2 and later)|https://github.com/FRIBDAQ/docs/tree/main/specbatch/index.md]]
- [[Documentation for SpecTcl's REST-like interface|https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/index.md]] (Updated October 21, 2025)
- [[Parallel SpecTcl (version 7.0+)|https://github.com/FRIBDAQ/docs/tree/main/parallel/index.md]]
- [[CutiePie (QtPy) Python-based displayer for
              SpecTcl 5.13-000|https://github.com/FRIBDAQ/docs/tree/main/qtpy/index.md]]
- [[Genx framework independent analysis|https://github.com/FRIBDAQ/docs/tree/main/genx/index.md]]
- [[SpecTcl Python scripting
  	    interface (5.3-000 and later).|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/python/index.md]]
- [[SpecTcl 5.10-006 introduces
  	    how to get a Root interpreter that knows about the
  	    spectra in a SpecTcl display (Xamine) shared memory.|https://github.com/FRIBDAQ/docs/tree/main/rootxamine/index.md]]
- [[SpecTcl Sqlite3 store|https://github.com/FRIBDAQ/docs/tree/main/spectcldb/index.md]]
  	    (SpecTcl 5.3 and later), provides an Sqlite3 based store for
  	    SpecTcl objects and pre-processed event data.
- [[Using SpecTcl with VMUSBReadout|https://github.com/FRIBDAQ/docs/tree/main/vmusbspectcl/index.md]]
- [[Using SpecTcl with data from fribdaq-readout (MVLC contoller)|https://github.com/FRIBDAQ/docs/tree/main/mvlcspectcl/index.md]]
- SpecTcl Plugin documentation


# FRIB Analysis Pipeline


The FRIB Analysis Pipeline models analysis of data from experiments
	 as a pipeline of transformations from raw data to increasingly
	 physically meaningful parameters.  It provides parallel tools
	 for stages of that pipeline.

Documentation for the current version of this software is available
	 at [[The FRIB Analysis Pipeline|https://github.com/FRIBDAQ/docs/tree/main/apipeline/index.md]]
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


- [[## Proceed to User's Guide|https://github.com/FRIBDAQ/docs/tree/main/ddas-12.1-001/index.md]]
  Note that this guide is specific to FRIBDAQ 12.0 and later; for legacy DDAS, see the [[Legacy User's Guide|https://github.com/FRIBDAQ/docs/tree/main/ddas-1.1/index.md]]
- [[DDAS Data Format in FRIBDAQ|https://github.com/FRIBDAQ/docs/tree/main/ddasformat-1.1-001/index.md]]
- [[DDASToys Documentation|https://github.com/FRIBDAQ/docs/tree/main/ddastoys-6.2-000/index.md]]
- [[PIXIE 16 hardware Manual|https://github.com/FRIBDAQ/docs/tree/main/pixie16/Pixie16_UserManual.pdf.md]]


# FRIBDAQ Support for GET electronics


The GET (Generalized Electronics for TPCs) is a high density electronics
   package that provides 100Mhz digitized signals.  Support for a single CoBo
   is now available for SPDAQ systems that are configured to interface with
   GET Micro-TCA crates. See:


### [[See the NSCLCDAQ GET documentation|https://github.com/FRIBDAQ/docs/tree/main/../get/index.md]]


# Rustogrammer a new histogramer


Rustogrammer is a new histograming package written in rust and portable
      to Windows.  With the Cutiepie displayer having been ported to windows
      and the availability of a portable PyQt front end that is similar to the
      Tree GUI available in SpecTcl, this package brings analysis power similar
      to SpecTcl to the desktop.

      See
      [[The comprehensive documentation|https://github.com/FRIBDAQ/docs/tree/main/rustogramer/index.md]]
