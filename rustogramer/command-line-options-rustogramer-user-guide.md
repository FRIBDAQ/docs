Provide site root to javascript 

 Work around some values being stored in localStorage wrapped in quotes 

 Set the theme before any content is loaded, prevents flash 


 Hide / unhide sidebar before it is displayed 


1. [[chapter_1]]
2. 1. [[chap1_1]]
3. [[chapter_2]]
4. 1. [[chap2_1]]
   2. [[chap2_2]]
5. [[chapter_3]]
6. [[chapter_4]]
7. 1. [[chap4_1]]
   2. [[chap4_2]]
   3. [[chap4_3]]
   4. [[chap4_4]]
   5. [[chap4_bindsets]]
   6. [[chap4_5]]
   7. [[chap4_6]]
   8. [[chap4_filters]]
   9. [[chap4_7]]
   10. [[chap4_8]]
8. [[chapter_5]]
9. [[chapter_6]]
10. 1. [[chap6_1]]
   2. [[chap6_2]]
11. [[chapter7]]
12. 1. [[chap7_1]]
   2. [[chap7_2]]
   3. 1. [[chap7_2_responses]]
      2. [[chap7_2_parameter]]
      3. [[chap7_2_rawparameter]]
      4. [[chap7_2_gates]]
      5. [[chap7_2_spectrum]]
      6. [[chap7_2_attach]]
      7. [[chap7_2_analyze]]
      8. [[chap7_2_apply]]
      9. [[chap7_2_ungate]]
      10. [[chap7_2_channel]]
      11. [[chap7_2_evbunpack]]
      12. [[chap7_2_filter]]
      13. [[chap7_2_fit]]
      14. [[chap7_2_fold]]
      15. [[chap7_2_integrate]]
      16. [[chap7_2_shmem]]
      17. [[chap7_2_sbind]]
      18. [[chap7_2_ubind]]
      19. [[chap7_2_mirror]]
      20. [[chap7_2_pman]]
      21. [[chap7_2_project]]
      22. [[chap7_2_pseudo]]
      23. [[chap7_2_roottree]]
      24. [[chap7_2_script]]
      25. [[chap7_2_treevariable]]
      26. [[chap7_2_version]]
      27. [[chap7_2_exit]]
      28. [[chap7_2_ringformat]]
      29. [[chap7_2_specstats]]
      30. [[chap7_2_swrite]]
      31. [[chap7_2_sread]]
      32. [[chap7_2_trace]]
   4. [[chap7_mirror]]
   5. [[chap7_3]]
   6. [[chap7_4]]
   7. [[chap7_5]]
   8. [[chap7_6]]
   9. [[chap7_7]]
13. [[apppendix_1]]






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


[[print]]





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
[[chapter7]]
[[chap7_2]]



[[chapter7]]
[[chap7_2]]









 Custom JS scripts
