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

# [/spectcl/sbind requests](#spectclsbind-requests)


SpecTcl and rustogrramer maintain a shared memory into which spectra can be put.  Such spectra can be accessed by local display programs providing a high speed channel to send histogram data to the displayer.


Spectra placed in shared memory are said to be *bound* to shared memory.  In SpecTcl, there is no cost to binding spectra, the spectrum bins are moved into shared memory and histograming directly occurs in shared memory.  In Rustogramer, the underlying histograming engine does not allow this so channels are periodically copied o that shared memory.


Note that `sbind` has its origins in the original SpecTcl where the more natural `bind` collides with the Tk `bind` command for binding events in display elements to scripts.


The `/spectcl/sbind` URI domain has the follwing URIs:


- [`/spectcl/sbind/all`](#spectclsbindall) - Bind all spectra to display memory.
- [`/spectcl/sbind/sbind`](#spectclsbindsbind) - Bind a single spectrum to the display.
- [`/spectcl/sbind/list`](#spectclsbindlist) - List th current bindings.
- [`/spectcl/sbind/set_update`](#spectclsbindset_update) Rustogramer only, specifies the number of seconds between updates to the shared memory.
- [`/spectcl/sbind/get_update`](#spectclsbindget_update) Rustogramer only, returns the shared memory refresh rate.


## [/spectcl/sbind/all](#spectclsbindall)


Binds all spectra to display memory.


### [Query parameters](#query-parameters)


No paramters are supported.


### [Response format detail](#response-format-detail)


A generic response is returned.


#### [Sample Responses.](#sample-responses)


```json
{
    "status": "OK",
    "detail" : ""
}

```


Failure is possible for example, if there is not sufficient free space in the shared memory region to accomodate all of the spectrum channels.  An error return from Rustogramer might look like


```json
{
    "status": "Unable to bind spectrum <aspectrum-name>",
    "detail": "<reason the bind failed>"
}

```


## [/spectcl/sbind/sbind](#spectclsbindsbind)


Bind some spectra to the display memory.


### [Query parameters](#query-parameters-1)


- **spectrum** (string) - Mandatory.  Names a spectrum to bind to the  display memory.  Note that if this query parameter appears more than once, all mentioned spetra will be bound.


### [Response format detail](#response-format-detail-1)


The response is a generic response.


#### [Sample Responses.](#sample-responses-1)


Success:


```json
{
    "status": "OK",
    "detail" : ""
}

```


Failure:


```json
{
    "status": "Unable to bind spectrum <aspectrum-name>",
    "detail": "<reason the bind failed>"
}

```


## [/spectcl/sbind/list](#spectclsbindlist)


List the spectrum bindings.


### [Query parameters](#query-parameters-2)


- **pattern** (string) - Optional glob pattern, only bindings for spectra with names that match the pattern will be listed.   The pattern defaults to `*` which matches all spectra.


### [Response format detail](#response-format-detail-2)


The **detail** is a vector of objects with the following attributes:


- **spectrumid** (unsigned)- A number associated with the spectrum (not really useful in most cases).
- **name**  (string) - Name of the spectrum.
- **binding** (unsigned) - The shared memory slot number containing the spectrum's description.


#### [Sample Responses.](#sample-responses-2)


Success with a single matching spectrum in slot 6:


```json
{
    "status" : "OK",
    "detail" : [
        {
            "spectrumid" : 12,
            "name"       : "a-spectrum",
            "binding"    : 6
        }
    ]
}

```


## [/spectcl/sbind/set_update](#spectclsbindset_update)


Available only on Rustogramer.  Provides the refresh period in seconds for the shared memory.  In SpecTcl, since histograms are directly incremented in display memory for bound spectra, this is not needed, however in Rustogramer, spectrum contents in shared memory must be refreshed from their histograms


### [Query parameters](#query-parameters-3)


- **seconds** (unsigned int) - Mandatory.  Provdes a new update period in seconds.


### [Response format detail](#response-format-detail-3)


A generic response.


#### [Sample Responses.](#sample-responses-3)


If attempted in SpecTcl you will get a `404` error from the server indicating there is no URL match.


Success:


```json
{
    "status" : "OK",
    "detail" : ""
}

```


## [/spectcl/sbind/get_update](#spectclsbindget_update)


Rustogramer only Queries the shared memor refresh period.


### [Query parameters](#query-parameters-4)


No query parameters are supported.


### [Response format detail](#response-format-detail-4)


The **detail** attribute is an unsigned integer that is the number of seconds between spectrum contents refreshes.


#### [Sample Responses.](#sample-responses-4)


```json
{
    "status" : "OK",
    "detail" : 2
}

```


The spectrum  memory is refreshed every `2` seconds.




 Mobile navigation buttons 
[[chap7_2_shmem]]
[[chap7_2_ubind]]



[[chap7_2_shmem]]
[[chap7_2_ubind]]









 Custom JS scripts
