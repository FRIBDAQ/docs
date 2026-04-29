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

# [/spectcl/evbunpack requests](#spectclevbunpack-requests)


This domain of URIs is only available in SpecTcl.  It works with the dynamic event processing pipeline to configure an event processor that can be used with data that was emitted from the FRIB/NSCLDAQ event builder.   The idea is that you can use the [[pipline manager|./chap7_2_pman]] to create event processing pipelines which you then associated with specific source ids using  this set of URIs.


Operations supported are:


- [/spectcl/evbunpack/create](#spectclevbunpackcreate) - Creating an event processor with pipeline slots for source ids.
- [/spectcl/evbunpack/add](#spectclevbunpackadd) - Associate an existing event processing pipeline with an source id.
- [/spectcl/evbunpack/list](#spectclevbunpacklist) - list the event builder event processors that have been created by this command.


For more information and background, see the **evbunpack** command in the
[SpecTcl command reference](https://docs.nscl.msu.edu/daq/newsite/spectcl-5.0/cmdref/index.html)


## [/spectcl/evbunpack/create](#spectclevbunpackcreate)


Creates a new event unpacker for event built data.  You can think of the unpacker as having a slot for each possible source id. Initially, all slots are empty.
Note that this operation creates and registers an event processor.  Such event processors can be put into pipelines just like any other event processor.


### [Query parameters](#query-parameters)


All parameters are mandatory


- ***name**  (string) - name of the event processing pipeline.  This must be unique.
- **frequency** (float) - Clock frequency of the timestamp.  This is used to create event builder diagnostic parameters.  The value of this parameter are in units of floating point MHz.  For examle 16.5  means 16.5MHz.
- **basename** (string) - Provides a basename for the diagnostic parameters.  For more information aobut the diagnostic parameters; see the documentation of `CEventBuilterEventProcessor` in the [SpecTcl Programming Reference](https://docs.nscl.msu.edu/daq/newsite/spectcl-5.0/pgmref/index.html).


### [Response format detail](#response-format-detail)


The response is a generic response


#### [Sample Responses.](#sample-responses)


Successful resopnse:


```json
{
    "status": "OK"
}

```


## [/spectcl/evbunpack/add](#spectclevbunpackadd)


Associates an exiting, registered event processor with a source-id.  Events with fragments that match the source id will invoke that pipeline, passed the fragment's payload.


### [Query parameters](#query-parameters-1)


All parameters are mandatory.


- **evpname**  (string) - Name of an event processor made via e.g. [/spectcl/evbunpack/create](#spectclevbunpackadd).
- **source** (unsigned) - Source id that will be associated with the next parameter.
- **pipe** (string) - Name of a registered event processor that will be run to process fragments from **source** in each event.  Note this is a badly named parameter.


### [Response format detail](#response-format-detail-1)


The response is a generic response.  On failure, the **status** contains `evbunpack addprocessor command failed` with **detail** set to the error message from that command.


#### [Sample Responses.](#sample-responses-1)


Success:


```json
{
    "status": "OK"
}

```


## [/spectcl/evbunpack/list](#spectclevbunpacklist)


Returns a list of event processors that are evbunpack event processors.


### [Query parameters](#query-parameters-2)


- **pattern** (string) - Optional glob pattern that filters out the list to only those names which match the pattern.


### [Response format detail](#response-format-detail-2)


The **detail** is an array of strings.  Each element is the name of an event builder unpacker.


#### [Sample Responses.](#sample-responses-2)


Success:


```json
{
    "status" : "OK",
    "detail" : [
        "s800",
        "lenda",
        "greta"
    ]
}

```




 Mobile navigation buttons 
[[**|chap7_2_channel]]
[[**|chap7_2_filter]]



[[**|chap7_2_channel]]
[[**|chap7_2_filter]]









 Custom JS scripts
