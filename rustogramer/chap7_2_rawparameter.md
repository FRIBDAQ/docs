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

# [/spectcl/rawparameter requests](#spectclrawparameter-requests)


For Rustogramer, the requests in this URI domain map to similar requests in the
[[/spectcl/parameter|./chap7_2_parameter]] domain.  For SpecTcl, however for historical reasons, there is a difference between a raw parameter and a tree parameter.


Originally tree parameters were  a contributed package written by Daniel Bazin.  Later, due to its utility, tree parameters were incorporated into supported SpecTcl code.  However a distinction does exist, internally between tree parameters and the original raw parameters, which may not be mapped to tree paramters.


In SpecTcl, therefor, these URIs manipulate raw parameters without affecting any tree parameters that might be bound to them.


The requests include:


- [`/spectcl/rawparameter/new`](#spectclrawparameternew) (Rustogramer maps this to [[`/spectcl/parameter/create`|./chap7_2_parameter#spectclparametercreate]]).  SpecTcl creates a new raw parameter.
- [`/spectcl/rawparameter/delete`](#spectclrawparameterdelete) (Rustogramer implements this).  This deletes an existing (raw) parameter.
- [`/spectcl/rawparameter/list`](#spectclrawparameterlist) (Rustogramer maps this to [[`spectcl/parameter/list`|./chap7_2_parameter#spectclparameterlist]])


## [/spectcl/rawparameter/new](#spectclrawparameternew)


Creates a new raw parameter.  Note that in Rustogramer, this is forwarded to the handler for [[`/spectcl/parameter/new`|./chap7_2_parameter#spectclparametercreate]]. Refer to that documentation.  This section documents how this URI is implemented for SpecTcl.


### [Query parameters](#query-parameters)


- ***name*** (required string) - Name of the parameter to be created.  The value of this parameter *must* not be the name of an existing parameter,
- **number** (required in SpecTcl  unsigned integer) - The parameter id to be assigned to the parameter.
- **resolution** (optional unsigned integer) - Number of bits of resolution in the metadata for the raw parameter.
- **low**, **high** (optional floats) -  Low and high limits for parameter values.
- **units** (optional string) - Units of measure metadata.


### [Response format detail](#response-format-detail)


On success, this just has **status** with the value `OK` .  On failure
***detail*** provides more information about the error.


#### [Sample Responses.](#sample-responses)


Successful completion:


```json
{
    "status" : "OK"
}

```


Attempt to redefine a parameter:


```json
{
    "status" : "'parameter -new' command failed",
    "detail" : "Duplicate Key during Dictionary insertion\nKey was:  event.raw.00 Id was: -undefined-\n"
}

```


*detail* is the error message from `parameter -new`  in this case it indicates that `event.raw.00` already exists and the request is attemptig to find it.


## [/spectcl/rawparameter/delete](#spectclrawparameterdelete)


Deletes a raw parameter.


### [Query parameters](#query-parameters-1)


One of the following parameters must be present, but not both.


- name (string) - Name of the parameter to delete.
- id (unsigned integer) - Number of the parameter to delete


### [Response format detail](#response-format-detail-1)


The response is a generic response, whith SpecTcl omitting **detail** if the operation succeded.


#### [Sample Responses.](#sample-responses-1)


Successful request:


```json
{
    "status" : "OK"
}

```


Delete a nonexistent parameter:


```json
{
    "status" : "'parameter -delete' command failed",
    "detail" : "Failed search of dictionary by Key string\nKey was:  aaaa Id was: -undefined-\n"
}

```


## [/spectcl/rawparameter/list](#spectclrawparameterlist)


Lists the raw parameters with names matching a pattern or a specific id.


### [Query parameters](#query-parameters-2)


One of the following are required


- pattern (string) pattern used to match the parameter names that will be listed. The pattern can contain any filename matching wild cards supported by the shell.
- id (unsigned integer) Number of the paramter to list.


### [Response format detail](#response-format-detail-2)


On success, **detail**  is an array of structs.  Each struct has the fields:


- **name** - name of the parameter being described.
- **id**  - Id of the parameter.
- **resolution** - Only present if the raw parameter has a resolution set. The integer resolution.
- **low** **high** - Only present if the raw parameter has low/high limits.  These are the floating point low and high limits.
- **units** - Only present if the raw parameter has units of measure. This is the units string.


#### [Sample Responses.](#sample-responses-2)


Successful return with one match `event.sum`


```json
{ 
    "status" : "OK", 
    "detail" : [
        { 
            "name" : "event.sum", 
            "id" : 10, 
            "units" : "arbitrary" 
        }
    ] 
}

```




 Mobile navigation buttons 
[[**|chap7_2_parameter]]
[[**|chap7_2_gates]]



[[**|chap7_2_parameter]]
[[**|chap7_2_gates]]









 Custom JS scripts
