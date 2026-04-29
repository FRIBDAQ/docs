Provide site root to javascript 

 Work around some values being stored in localStorage wrapped in quotes 

 Set the theme before any content is loaded, prevents flash 


 Hide / unhide sidebar before it is displayed 


1. [[**1.** Chapter 1 - Introduction|chapter_1]]
2. 1. [[**1.1.** How to use this book|chap1_1]]
3. [[**2.** Chapter 2 - Preparing data for Rustogramer|chapter_2]]
4. 1. [[**2.1.** The FRIB analysis pipeline|chap2_1]]
   2. [[**2.2.** Format of data Rustogramer accepts|chap2_2]]
5. [[**3.** Chapter 3 - Running Rustogramer|chapter_3]]
6. [[**4.** Chapter 4 - Using the Rustogramer GUI|chapter_4]]
7. 1. [[**4.1.** The Spectra Tab|chap4_1]]
   2. [[**4.2.** The Parameters Tab|chap4_2]]
   3. [[**4.3.** The Variables Tab|chap4_3]]
   4. [[**4.4.** The Gate Tab|chap4_4]]
   5. [[**4.5.** The BindSets Tab|chap4_bindsets]]
   6. [[**4.6.** The File Menu|chap4_5]]
   7. [[**4.7.** The Data Source Menu|chap4_6]]
   8. [[**4.8.** The Filters Menu|chap4_filters]]
   9. [[**4.9.** The Spectra Menu|chap4_7]]
   10. [[**4.10.** The Gate Menu|chap4_8]]
8. [[**5.** Chapter 5 - Using CutiePie to display histograms|chapter_5]]
9. [[**6.** Chapter 6 - the REST interface|chapter_6]]
10. 1. [[**6.1.** Tcl REST interface|chap6_1]]
   2. [[**6.2.** Python REST interface|chap6_2]]
11. [[**7.** Chapter 7 - Reference material|chapter7]]
12. 1. [[**7.1.** Command Line Options|chap7_1]]
   2. [[**7.2.** REST requests and responses|chap7_2]]
   3. 1. [[**7.2.1.** Response format|chap7_2_responses]]
      2. [[**7.2.2.** /spectcl/parameter requests|chap7_2_parameter]]
      3. [[**7.2.3.** /spectcl/rawparameter requests|chap7_2_rawparameter]]
      4. [[**7.2.4.** /spectcl/gate requests|chap7_2_gates]]
      5. [[**7.2.5.** /spectcl/spectrum requests|chap7_2_spectrum]]
      6. [[**7.2.6.** /spectcl/attach requests|chap7_2_attach]]
      7. [[**7.2.7.** /spectcl/analyze requests|chap7_2_analyze]]
      8. [[**7.2.8.** /spectcl/apply requests|chap7_2_apply]]
      9. [[**7.2.9.** /spectcl/ungate requests|chap7_2_ungate]]
      10. [[**7.2.10.** /spectcl/channel requests|chap7_2_channel]]
      11. [[**7.2.11.** /spectcl/evbunpack requests|chap7_2_evbunpack]]
      12. [[**7.2.12.** /spectcl/filter requests|chap7_2_filter]]
      13. [[**7.2.13.** /spectcl/fit requests|chap7_2_fit]]
      14. [[**7.2.14.** /spectcl/fold requests|chap7_2_fold]]
      15. [[**7.2.15.** /spectcl/integrate requests|chap7_2_integrate]]
      16. [[**7.2.16.** /spectcl/shmem requests|chap7_2_shmem]]
      17. [[**7.2.17.** /spectcl/sbind requests|chap7_2_sbind]]
      18. [[**7.2.18.** /spectcl/unbind requests|chap7_2_ubind]]
      19. [[**7.2.19.** /spectcl/mirror requests|chap7_2_mirror]]
      20. [[**7.2.20.** /spectcl/pman requests|chap7_2_pman]]
      21. [[**7.2.21.** /spectcl/project requests|chap7_2_project]]
      22. [[**7.2.22.** /spectcl/psuedo requests|chap7_2_pseudo]]
      23. [[**7.2.23.** /spectcl/rootree requests|chap7_2_roottree]]
      24. [[**7.2.24.** /spectcl/script requests|chap7_2_script]]
      25. [[**7.2.25.** /spectcl/treevariable requests|chap7_2_treevariable]]
      26. [[**7.2.26.** /spectcl/version requests|chap7_2_version]]
      27. [[**7.2.27.** /spectcl/exit requests|chap7_2_exit]]
      28. [[**7.2.28.** /spectcl/ringformat requests|chap7_2_ringformat]]
      29. [[**7.2.29.** /spectcl/specstats requests|chap7_2_specstats]]
      30. [[**7.2.30.** /spectcl/swrite requests|chap7_2_swrite]]
      31. [[**7.2.31.** /spectcl/sread requests|chap7_2_sread]]
      32. [[**7.2.32.** /spectcl/trace requests|chap7_2_trace]]
   4. [[**7.3.** Shared memory Mirror service|chap7_mirror]]
   5. [[**7.4.** Tcl REST reference|chap7_3]]
   6. [[**7.5.** Python REST reference|chap7_4]]
   7. [[**7.6.** Looking at the Rustogramer internals documentation|chap7_5]]
   8. [[**7.7.** Schema of configuration files|chap7_6]]
   9. [[**7.8.** Format of JSON Spectrum contents files|chap7_7]]
13. [[**8.** Appendix I - Installing Rustogramer|apppendix_1]]






 Track and set sidebar scroll position 

**


**

- Light
- Rust
- Coal
- Navy
- Ayu



**


# Rustogramer User Guide


[[**|print]]





 Apply ARIA attributes after the sidebar and the sidebar toggle button are added to the DOM 

# [Chapter 3 - Running Rustogramer](#chapter-3---running-rustogramer)


Rustogramer tries to be compatible with NSCLSpecTcl in several ways:


- It supports the most commonly used spectrum types defined by SpecTcl
- It supports the most commonly used condition (gate) types defined by SpecTcl
- It implements a REST server that is highly compatible with SpecTcl's allowing clients to work both with SpecTcl and Rustogramer.
- It implements a share display memory that has a structure that is compatible with SpecTcl's, though rather than placing that shared memory in a SYSV shared memory segment, the `mmap` subsystem which maps shared memory to ordinary files is used.
- It implements a mirror server that allows remote clients to create a mirror of the display memory in remote systems.
- It can either user hard coded port values for its servers or it can use the NSCLDAQ port manager software to allocated a named service.


For simplicity, we assume that rustogramer was installed in `/usr/opt/rustogramer/version`
In practice, `version` in the path above would be a rustogramer version string of the form a.b.c where a,b,c are integers.


## [Running rustogramer with hard coded server port values.](#running-rustogramer-with-hard-coded-server-port-values)


Before you take this approach note that you'll need to assign port numbers that are unique system wide.  That means you must avoid port numbers used by other instances of rustogramer you run in your system as well *those run by other users*.  This can be very difficult and is why we recommend that
you use the NSCLDAQ port manager to assign and advertise services.  See
[the next section](#using-the-port-manager-to-assign-server-port-values) below for a description of this process and the prerequisites it requires.


The rustogramer command is in the `bin` directory of the rustogramer installation tree and is named `rustogrammer` (note  the doubled m). The command accepts serveral options that are described fully in [[Command Line Options|./chap7_1]].  To run with manuall assigned ports you'll need:


- `--shm-mbytes` (which can be abbreviated `-s`).  The value that follows this option are the number of megabytes of shared spectrum memory rustogramer will create.  Note that you must have sufficient disk quota in your home directory to support the creation of the shared memory file.  If not specified, this defaults to `32`
- `--rest-port` (which can be abbreviated `-r`).  Specifies the port on which the REST server will listen for connections.  This defaults to `8000`.
- `--mirror-port` Specifies the port on which the shared memory mirror server listens for connections.  This defaults to `8001`.


Typically, then to run rustogramer with hard coded port values you choose the amount of spectrum memory you will need, assign prot values for the REST and mirror servers and supply appropriate values to the options above.  Given the defaults; if `rustogrammer` is in your path:


```bash
rustogramer

```


is equivalent to


```bash
rustogrammer --shm-mbytes 32 --rest-port 8000 --mirror-port 8001

```


## [Using the port manager to assign server port values](#using-the-port-manager-to-assign-server-port-values)


The NSCLDAQ port manager can be run to reduce the work you have to do to ensure that rustogramer ports are uniquely chosen.  The port manager assigns free ports from a pool it maintains and associates them with a name (service name) and the user whose program made the request.  As long as the program holds the connection over which it asked for a port open, the port remains allocated to the requester and clients can interact with the port manager to translate service name/user pairs into port numbers.


Where possible, this is the recommended way to use rustogramer.   Rustogramer knows that the port manager itself has allocated port `30000` and can interact with it by making connections to that port.


You still must take care that for every instance of rustogramer *you* run within a single system, you choose a unique service name.  You don't have to worry about choosing a unique name across all system users, but, if you run rustogramer more than once in a single system, you need unique service names for each rustogramer.


You can specify service names using the `--rest-service` and `--mirror-service` command line options rather than the `---rest-port` and `--mirror-port` options described in
[Using hard coded values](#running-rustogramer-with-hard-coded-server-port-values) above.
There are no default values for these options.  Supplying these options will override any port values you may have otherwise specified.  Here's a sample command line:


```bash
rustogrammer --shm-mbytes 128 --rest-service RG_REST --mirror-service RG_MIRROR

```


It runs rustogramer creating a 128 Megabytes spectrum memor region, and allocates/advertises with the port manager:


- RG_REST - for the REST server.
- RG_MIRROR - for the mirror server.


At any run of rustogramer with these values the actual ports allocated may vary.  Note that if another user runs rustogramer with the same service names, there is no collision as the NSCLDAQ port manager qualifies the service name with a username so, if my username is `rusty` and another user named `graham` runs rustogramer in the same way, four distinct ports wil be allocated and advertised as:


```
| Service   |  user  | 
|--------------------|
| RG_REST   | rusty  |
| RG_MIRROR | rusty  |
| RG_REST   | graham |
| RG_MIRROR | graham |

```


If `graham` looks up the port `RG_REST` he'll get the port his rustogramer rserved and `rusty` will get the one she allocated.




 Mobile navigation buttons 
[[**|chap2_2]]
[[**|chapter_4]]



[[**|chap2_2]]
[[**|chapter_4]]









 Custom JS scripts
