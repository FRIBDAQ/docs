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

# [/spectcl/shmem requests](#spectclshmem-requests)


Returns information about the shared Spectrum shared memory. Both SpecTcl and Rustogramer can *bind* histograms into shared memory.  When they do this, external programs can map that same shared memory and e.g. render the histograms graphically.


The following URIs are supported in this domain:


- [`/spectcl/shmem/key`](#spectclshmemkey) Get shared memory attachment information
- [`/spectcl/shmem/size`](#spectclshmemsize) Get the total size of the shared memory region.
- [`spectcl/shmem/variables`](#spectclshmemvariables) Provide the values of some "interesting" shared memory variables.


## [/spectcl/shmem/key](#spectclshmemkey)


This URI provides information about how to attach to the server's shared memory.  Historically, SpecTcl used SYSV shared memory segments.  These are identified by a 4byte key (SpecTcl uses ASCII bytes for these bytes so they are printable).


SYSV shared memory, however is not portable.  There are two other forms of shared memory:


- POSIX shared memory
- File mapped shared memory.


Of these, rustogramer chose the latter.  One problem, therefor was how to identify the method to use to map the shared memory from a "key".  A key, therefore, can either look like:


- *kkkk*  - a four character string, in which case it identifies a SYSV shared memory key.
- sysv:*kkkk* - which identifies a sysV shared memory.
- posix:*filename* - which identifies a POSIX shared memory region.
- file:*filename* - which identifies a file backed shared memory.


### [Query parameters](#query-parameters)


None


### [Response format detail](#response-format-detail)


The resonse is a generic response.  On success, **detail** will be the shared memory key.


#### [Sample Responses.](#sample-responses)


SpecTcl success:


```json
{
    "status" : "OK",
    "detail" : "XA7c"
}

```


Rustogramer success:


```json
{
    "status" : "OK",
    "detail" : "file:/home/ron/.tmpabcde"
}

```


Rustogramer failure:


```json
{
    "status": "Failed to get shared memory name",
    "detail": "<reason for the failure"
}

```


Note that SpecTcl always succeeds.


## [/spectcl/shmem/size](#spectclshmemsize)


Returns the size of the display shared memory in bytes.


### [Query parameters](#query-parameters-1)


None


### [Response format detail](#response-format-detail-1)


*detail* is the stringified size in bytes.


#### [Sample Responses.](#sample-responses-1)


Success:


```json
{
    "status" : "OK",
    "detail" : "209715200"
}

```


In this case the entire shared memory region, headers and spectrum channels  is `209715200` bytes.


## [/spectcl/shmem/variables](#spectclshmemvariables)


Provides the values of some internal SpecTcl variables.  Note that


### [Query parameters](#query-parameters-2)


No query parameters are  supported.


### [Response format detail](#response-format-detail-2)


The **detail** is an object where each field is a name/value of an internal variable.  Note that some of the variables are not supported by Rustogramer but are provided with a "sensible" value.  The list below will point out when this is the case.  Note that all variable values are strings the types given  are hints about how to interpret the srings.  For example **DisplayMegabytes** could be "200"  which means 200.


The attributes are:


- **Displaymegabytes** (unsigned) - Megabytes of shared memory spectrum storage.
- **OnlineState** (bool) - set `true` by some SpecTcl scripts that use `attach -pipe` to attach to the online DAQ system.  Rustogramer sets this to `false`
- **EventListSize** - The size of the event batch.  For SpecTcl this is the number of decoded events sent on each histogramming operation. For Rustogramer, the number of event ring items sent to the histogram thread in each operation.
- **ParameterCount** (unsigned/string)- In SpecTcl, this is the initial size used for `CEvent` objects, while for Rusgtogramer this is the value "-undefined-"
- **SpecTclHome** (string) - SpecTcl - the top level of the installation directory tree. for Rustogramer, this is the directory in which the executable was installed.
- **LastSequence** (unsigned/string) - Number of ring items processed in the most recent run for SpecTcl, for Rustogramer, this is "--undefined-"
- **RunNumber** (unsigned/string) - for SpecTcl, this is the run number of the most recently seen state change ring item.  For rustogramer this is "-undefined-"
- **RunState** (int/string) - For SpecTcl this is nonzero if analysis is active or zero if not.  For Rustogramer this is "-undefined-".
- **DisplayType** (string) - For SpecTcl this identifies the type of the displayer, e.g. `qtpy`.  Rustogramer has no integrated displayer so it always returns `None` to be consistent with headless SpecTcl.
- **BuffersAnalyzed** (unsigned/string) - The total number of ring items analyzed.  For SpecTcl, taken with **LastSequence** the fraction of events analyzed can be computed.  Rustogramer returns "-undefined-"
- **RunTitle** (string) - Title from the most recent state change item for SpecTcl, "-undefined-" for rustohgramer.


The following statistics attributes are present in SpecTcl but not in Rustogramer:


- **Statistics(EventsRejectedThisRun)** (unsigned) - Number of eevents for which the event processing pipeline returned `kfFALSE` in this run.
- **Statistics(RunsAnalyzed)** - Number of times a `BEGIN_RUN` ring item was seen when analyzing data.
- **Statistics(EventsAnalyzed)** - Number of events analyzed.
- **Statistics(EventsAccepted)** - Number of events for which the event processing pipline returned `kfTRUE`
- **Statistics(EventsAnalyzedThisRun)** - Number of events analyzed in the current run.
- **Statistics(EventsRejected)** - Total number of events for which the event processing pipeline returned `kfFALSE`.
- **Statistics(EventsAcceptedThisRun)** - Number of  events in this run for which the event processing pipeline retunrned `kfTRUE`


#### [Sample Responses.](#sample-responses-2)


SpecTcl:


```json
{
    "status" : "OK",
    "detail" : {
        "DisplayMegabytes"                  : "200",
        "OnlineState"                       : ">>> Unknown <<<",
        "EventListSize"                     : "1",
        "ParameterCount"                    : "256",
        "SpecTclHome"                       : "/usr/opt/spectcl/5.14-000",
        "LastSequence"                      : "0",
        "RunNumber"                         : "0",
        "RunState"                          : "0",
        "DisplayType"                       : "qtpy",
        "BuffersAnalyzed"                   : "1",
        "RunTitle"                          : ">>> Unknown <<<",
        "Statistics(EventsRejectedThisRun)" : "0",
        "Statistics(RunsAnalyzed)"          : "0",
        "Statistics(EventsAnalyzed)"        : "0",
        "Statistics(EventsAccepted)"        : "0",
        "Statistics(EventsAnalyzedThisRun)" : "0",
        "Statistics(EventsRejected)"        : "0",
        "Statistics(EventsAcceptedThisRun)" : "0"
    }
}

```




 Mobile navigation buttons 
[[**|chap7_2_integrate]]
[[**|chap7_2_sbind]]



[[**|chap7_2_integrate]]
[[**|chap7_2_sbind]]









 Custom JS scripts
