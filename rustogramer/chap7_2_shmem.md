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
[[chap7_2_integrate]]
[[chap7_2_sbind]]



[[chap7_2_integrate]]
[[chap7_2_sbind]]









 Custom JS scripts
