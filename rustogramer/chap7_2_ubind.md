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

# [/spectcl/unbind requests](#spectclunbind-requests)


For more information about spectrum binding, see [[./chap7_2_sbind]].


This domain of URIs supports a few methods for unbinding spectra.


- [`/spectcl/unbind/byname`](#spectclunbindbyname) - Unbind given the name of a spectrum.
- [`/spectcl/unbind/byid`](#spectclunbindbyid) - (SpecTcl only) - by spectrum id.
- [`/spectcl/unbind/all`](#spectclunbindall)  - Unbind all spectra.]


## [/spectcl/unbind/byname](#spectclunbindbyname)


Give a spectrum name, removes it from spectrum memory.  The spectrum still exists and is incremented, however clients of the shared memory are blind to it.


### [Query parameters](#query-parameters)


- **name** (string)  - mandatory name of the spetrum to unbind.


### [Response format detail](#response-format-detail)


A generic response is produced.


#### [Sample Responses.](#sample-responses)


Success:


```json
{
    "status" : "OK",
    "detail" : ""
}

```


Failure


```json
{
    "status": "Failed to unbind <spectrum-name>",
    "detail": "<reason unbind failed>"
}

```


## [/spectcl/unbind/byid](#spectclunbindbyid)


This is only supported in SpecTcl.  Unbinds a spectrum from the shared memory given its spectrum id.


### [Query parameters](#query-parameters-1)


- **id** (unsigned) - mandatory parameter that provides the id of the spectrum to unbind.


### [Response format detail](#response-format-detail-1)


Generic response.


#### [Sample Responses.](#sample-responses-1)


Rustogramer:


```json
{
    "status" : "Unbind by id is not implemented",
    "detail" : "This is not SpecTcl"
}

Spectcl success:

```json
{
    "status" : "OK"
}

```


## [/spectcl/unbind/all](#spectclunbindall)


Unbinds all bound spectra from shared memory.


### [Query parameters](#query-parameters-2)


No query parameters are supported.


### [Response format detail](#response-format-detail-2)


A generic response is returned.


#### [Sample Responses.](#sample-responses-2)


```json
{
    "status" : "OK"
}

```




 Mobile navigation buttons 
[[chap7_2_sbind]]
[[chap7_2_mirror]]



[[chap7_2_sbind]]
[[chap7_2_mirror]]









 Custom JS scripts
