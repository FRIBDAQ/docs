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

# [Command Line Options](#command-line-options)


## [Rustogramer command line options](#rustogramer-command-line-options)


Rustogramer supports a few command line arguments.  These arguments are inthe form of options that have a long form and, in some cases a short form.  Many options also have default values:


If you run rustogramer with the  --help option
(e.g. on linux /usr/opt/rustogramer/bin/rustogramer --help) you will get a summary of the command line options.


- --shm-mbytes (short form -s)  the value of this option is the number of megabytes of shared spectrum memory that will be created by rustoramer when it starts up.   The default value is 32 (32 Megabytes).  The maximum value is system dependent.  Rustogramer creates the shared memory using mmap backed up ordinary files.   This was, as near as I could tell, the only portable shared memory interface between windows and Linux.  If rustogramer exits cleanly (you tell it to exit using the GUI e.g.) these files get cleaned up by rustogramer.  If not, they are in the home directory on Linux and `\Users\username` on Windows where *username* is your windows username.  They will have names like `.tmp`*6chars*   where *6chars* means 6 random characters.   Note as well that in addition to the requested spectrum memory size, rustogramer will allocate a significant amount of additional storage for spectrum descsriptions.  If your home directory is in a file system with quotas enforced, you'll need to have sufficient free quota to create these files.
- --rest-port (short form -r) the value of this option is the port on which rustogramer's REST server will listen for connections.  The default value of this option is `8000`.  Where possible, you are encouraged to use the --rest-service option instead.
- --rest-service - provides  a service name which Rustogramer will advertise with the NSCLDAQ port manager.  If the NSCLDAQ port manager is not running; rustogramer will fail.  There is no short form and no default for this option.
- ---mirror-port - The value of this option is the port on wich rustogramer's mirror server will listen.  This has no short form and defaults to `8001` though again, where possible, you are encouraged to use --mirror-service (see below).
- --mirror-service - The value of this option is the service name that rustogramer will use to advertise the mirror servers.   This has no default.


Examples, assuming rustogramer is in the path:


```bash
rustogramer  --shm-mbytes 100 --rest-service RUSTO_REST --mirror-service RUSTO_MIRROR

rustogramer --rest-port 10000 --mirror-port 10001 -s 128

```


## [GUI Command line options.](#gui-command-line-options)


The GUI allows you to specify command line options that control how it connects to Rustogramer or SpecTcl.  These have short forms and long forms and, in some cases, default values.  The `--help` option will display a summary of the options e.g.


```bash
/usr/opt/rustogramer/bin/gui --help

```


- --host (short option -H) the value of this option is the host in which rustogramer or SpecTcl are running.
- --port (Short option -p), the value of this option is the numeric port on which rustogramer or SpecTcl is listening for REST requests.   Default is 8000
- --service (Short option -s) the service on which the REST server of rustogramer or SpecTcl has advertised with the NSCLDAQ port manager if that's how it got its server port.
- --user (short option -u)  Username under which Rustogramer/SpecTcl is running.  This is only needed if you are using the --service option to translate the port.  This defaults to your logged in user name.


Examples (assuming the gui is in the path):


```bash
gui --host localhost --service RUSTO_REST
gui --host localhost --port 8000

```




 Mobile navigation buttons 
[[**|chapter7]]
[[**|chap7_2]]



[[**|chapter7]]
[[**|chap7_2]]









 Custom JS scripts
