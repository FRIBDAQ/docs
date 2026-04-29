|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="vmetclintro"></a>Chapter 5. Tcl access to the VME via the SBS interface

The NSCL uses the Tcl/Tk scripting language to provide user interfaces
        and high level logic when speed is not critical.  This chapter descdribes
        a Tcl loadable package that provides access to VME crates attached to
        data takings systems via the SBS fiber optic interface.

This chapter is divided into the following sections.



Incorporating vmetclDescribes the environnment variables
                        and script additions you must make to use the
                        VME Tcl package.

Using vmetclProvides some samples that illustrate the use of
                        the VME tcl package.


For detailed reference information on the Vme Tcl package start with
        [[r10378]].

# <a name="AEN357"></a>5.1. Incorporating Vme Tcl in your scripts

In order to describe this for laboratories that have made different
            installation choices than the NSCL, we will assume the existence of
            an environment variable DAQROOT which points to
            the top of the installation tree for nscldaq. Consult with your local
            experts/installers for the value that must be given this variable.

The Tcl scripting language supports lodable packages.  This support
            includes support for a directory search path  to satisfy a package
            load request.  This search path can be set either via the
            TCLLIBPATH environment variable, which is a
            space separated list of directories to search, or by manipulating the
            `auto_path` script global variable.

The following bash shell script fragment appends the NSCLDAQ Tcl
            package repository to any existing TCLLIBPATH
            definition.

<a name="AEN366"></a>**Example 5-1. Appending the NSCLDAQ Tcl Package repository to Tcl's search
            path**

```
export TCLLIBPATH="$TCLLIBPATH $DAQROOT/TclLibs"
                
```

This can also be done at the script level:

<a name="AEN370"></a>**Example 5-2. Appending NSLCDAQ's TclPackage repository to Tcl's search path**

```
global env         # Needed if in a proc.
lappend auto_path [file join $env(DAQROOT) TclLibs]
                
```

Regardless of the method you use to add the NSCDAQ Tcl package
            repostory to the Tcl package search list, you must explicitly
            request the package from your script as follows:

<a name="AEN374"></a>**Example 5-3. Requesting the VME Tcl package be loaded.**

```
package require Vme
                
```

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Command line access to CAMAC via the SBS interface | Up | Sample programs that use the package |
