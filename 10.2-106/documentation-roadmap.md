|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 1. Introduction | Next |


---

# <a name="AEN180"></a>1.3. Documentation roadmap

This document can be logically divided into two segments.  The
            first segment consists of parts that are introductory material to
            various software tools.  The second segment provides extensive
            reference information in Unix Manpage format.

Installations of the software include the web documentation
            which is installed at
            $DAQROOT/share/html/index.html.
            Manual pages aer installed at
            $DAQROOT/share/man, so that
            e.g. ** man -M/usr/opt/daq/10.0/share/man spectcldaq**
            will display the manpage for the spectcldaq
            utility.

## <a name="AEN188"></a>1.3.1. Introductory Material

The introductory material is divided into several parts.  Introductory
                material is only generated as html pages in the
                web documentation.  It does not appear in the generated mapages.



commandsDocuments a few free standing commands that tie the ring buffer
                        data acquisition system togehter.

utilitiesDocuments the bulk of the shell command utilities.

librariesProvides introductory material for the major libraries
                        that define the API to subsystems of the DAQ software.

serversProvides documentation on the persistent servers the system.
                        Note that serveral utilities are transient client/server
                        applications, however these are not documented in
                        this section.

frameworksSeveral of the more complex API's are provided as
                            application frameworks.  This section describes
                            those frameworks.

## <a name="AEN213"></a>1.3.2. Manpage sections.

Manpage sections provide detailed reference material for
                components of the system.  In keeping with unix conventions,
                sections starting with 1 document commands
                that can be issued fromt he shell, sections beginning with
                3 document libraries and frameworks.
                Sections beginning with 5 document configuration
                files and file formats.



1compatibilityThe ring buffer data acuisition system provides serveral
                            utiltities that make migration to it from nscldaq-8.x
                            easy.  Specifically, there are a set of utilities
                            that provide the ability to hook clients that
                            are used to seeing nscldaq-8.x style buffer formats
                            tothe ring buffer daq.  This section provides manpages
                            for the full utility suite.
                            The utilities are provided both as toolkit elements
                            that can be used in unix pipelines and as scripts
                            that build commonly used pipelines.  This section
                            descsribes both of these types of elements.

1daqDocuments commands that you will use explicitly or
                            implicitly to build up your data acquisition system
                            configuration. In some cases you may never directly
                            invoke tools described in this section
                            (e.g. ringtostdout), in other
                            cases (e.g. ReadoutGui),
                            these applications will be an integral part of the
                            system and you will interact with them heavily.

1tclThis section describes several pure Tcl applications.
                            There is some overlap between this section and
                            1daq.  For example, this section describes
                            ScalerDisplay which,
                            while it is a pure Tcl application might just as
                            easily belong in the 1daq section.

1sbsReadoutProvides reference material that describes how you can
                            invoke the SBS readout framework you have built
                            to read data from your experiment.  While, in general,
                            the default invocation (without specifying options)
                            is appropriate, for special application you may
                            want to provide command line options to alter
                            how the Readout program operates.

1usbReadoutDocuments the USB Readout frameworks. The
                            VMUSB/CCUSB Readout frameworks provide high performance
                            access to VME and CAMAC crates.  These frameworks
                            allow you to describe the experiment in terms
                            of a set of digitizers, their configurations and
                            their readout orders.  Coupled with a special
                            version of SpecTcl, you can use this software to
                            use a single configuration file to get from readout
                            to raw spectra without a single line of C++ code.

3daqDescribes the bulk of the C++ classes that are provided
                            for various stand alone APIs.

3tclDescribes Tcl loadable packages you can use in your
                        Tcl scripts.

3sbsReadoutDescribes classes that are specifically part of
                            the SBS readout application framework.
                            Note that device support is described in
                            3daq, but classes you will interact with that
                            are specific to the readout framework are described
                            in this section.

3usbReadoutMost likely you don't need to read the man pages in this
                            section.  They provide reference documentation for the
                            classes that make up the VM/CC usb readout framework.
                            While at present only the VM-USB is supported, the
                            framework is generic enough that CC-USB support
                            can be built on top of it as well.

5tclDescribes configuration file formats and contents
                            for several Tcl utilities that require configuration
                            files.  In general the utilities that use configuration
                            files documented in this section will have references
                            to these pages.  In the web version of this document,
                            those references will be hyperlinks.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Overview of ring buffer utilities | Up | commands |
