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

# [/spectcl/evbunpack requests](#spectclevbunpack-requests)


This domain of URIs is only available in SpecTcl.  It works with the dynamic event processing pipeline to configure an event processor that can be used with data that was emitted from the FRIB/NSCLDAQ event builder.   The idea is that you can use the [[./chap7_2_pman]] to create event processing pipelines which you then associated with specific source ids using  this set of URIs.


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
[[chap7_2_channel]]
[[chap7_2_filter]]



[[chap7_2_channel]]
[[chap7_2_filter]]









 Custom JS scripts
