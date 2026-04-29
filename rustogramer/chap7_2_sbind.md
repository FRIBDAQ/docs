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
[[**|chap7_2_shmem]]
[[**|chap7_2_ubind]]



[[**|chap7_2_shmem]]
[[**|chap7_2_ubind]]









 Custom JS scripts
