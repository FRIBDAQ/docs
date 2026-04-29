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

# [parameter requests](#parameter-requests)


The base URI for these, after the `protocol//host:port` stuff is `/spectcl/parameter`
Several operations are supported on parameters:


- [`/list`](#spectclparameterlist) - lists the parameters and their properties.
- [`/edit`](#spectclparameteredit) - Modifies the metadata associated with a parameter.
- [`/promote`](#spectclparameterpromote) - Promote a raw parameter to a tree parameter.
- [`/create`](#spectclparametercreate) - Create a new parameter (Rustogramer only)
- [`/listnew`](#spectclparameterlistnew) - lists parameters that have modified metadata.
- [`/check`](#spectclparametercheck) - Checks the modified state of parameters.
- [`/uncheck`](#spectclparameteruncheck) - Turns off the modified state of parameters.
- [`/version`](#spectclparameterversion) - Provides version information about the capabilities of the parameter system (earlier versions of the SpecTcl `treeparameter` did not support the `-create` operation).


## [/spectcl/parameter/list](#spectclparameterlist)


Lists the parameters that are defined along with their metadata


### [Query parameters](#query-parameters)


- `filter` (optional) if provided the value of this query parameter is a patter that must be matched by the parameter name in order for it to appear in the response.  The filter string can include filesystem matching wild-card characters (e.g. `*` or `.`).  If the `filter` query parameter is not supplied, it will default to `*` which will match all parameters.


### [Reponse format detail](#reponse-format-detail)


The **detail** field of the response is a possibly empty array of parameter descriptions.  Each parameter description is, itself, a struct.  It is not an error for the filter string not to match any parameters.  That case results in an `OK` status with an empty array as the **detail**


Each parameter description is a struct with the following keys:


- **name** - Name of the parameter being described.
- **id** - An integer id that is assigned to the parameter.  The id is used in the histograming engine to specify the parameter.
- **bins** - Suggested binning for axes that are defined on the parameter.
- **low**  - Suggested low limit for axes that are defined on the parameter.
- **hi**   - Suggested high limit for axes that are defined on the parameter.
- **units** - Units of measure for the parameter (these are for documentation purposes only).
- **description** - (Rustogramer only) A description that documents the parameter purpose.  In SpecTcl, this field is missing.


#### [Sample Responses.](#sample-responses)


A single parameter matches  the filter.


```json
{
  "status" : "OK",
  "detail" : [{
      "name"        : "event.sum",
      "id"          : 10,
      "bins"        : 100,
      "low"         : 1,
      "hi"          : 100,
      "units"       : "arbitrary",
      "description" : "Sum over the arraay event.raw.nn"
  }]
}

```


Here is what you will get if your filter does not match any parameters


```json
{
  "status" : "OK",
  "detail" : []
}

```


Note how the **detail** field is just an empty array.


## [/spectcl/parameter/edit](#spectclparameteredit)


This request lets you modify the metadata associated with a parameter.


### [Query parameters](#query-parameters-1)


- **name** (Required string) - Name of the parameter to modify.
- **low** (Optional float) New value for the suggested axis low limit.
- **high** (Optional float) New value for the suggested axis high limit.
- **bins** (Optional unsigned integer) New value for the suggested axis binning.
- **units** (Optional string) New value for the parameters units of measure.
- **description** (Optional string -ignored by SpeTcl) - A description that documents the purpose of the parameter


### [Reponse format detail](#reponse-format-detail-1)


- Rustogramer returns a generic response.  SpecTcl, returns only a **status** on success, but the detail field is present on error.  Rustogramer always returns a **detail** field and on success it is an empty string.


#### [Sample Responses.](#sample-responses-1)


Successful return (Rustogramer):


```json
{
    "status" : "OK",
    "detail" : ""
}


```


Successful return (SpecTcl)


```json
{
    "status" : "OK"
}

```


Failure return for both Rustogramer and SpecTcl


```json
{
    "status" : "not found",
    "detail" : "event.raw"
}

```


## [/spectcl/parameter/promote](#spectclparameterpromote)


In SpecTcl, there is a distinction between parameters with metadata (tree parameters) and parameters without metadata (raw parameters). In Rustogramer all parameters have metadata.  For


- Rustogramer - this is equivalent to the [/spectcl/parameter/edit](#spectclparameteredit) operation.
- SpecTcl - this makes a treeparameter from a raw parameter.


### [Query parameters](#query-parameters-2)


- **name** (required String) - Name of the parameter to promote.
- **bins** (required for SpecTcl, optional for Rustogramer unsigned int) - The recommended bins for the promoted parameter.
- **low** (required for SpecTcl, optional for Rustogramer float) - The recommended low value for the promoted parameter.
- **high** (required for SpecTcl, optional for Rustogramer float) - The new high value for the promoted parameter.
- **units** (optional string) - Units of measure string for the promoted parameter.
- **description** (Rustogramer only String) - New desciption for the parameter


### [Reponse format detail](#reponse-format-detail-2)


The response is a Generic response.


#### [Sample Responses.](#sample-responses-2)


Note again that SpecTcl may omit the **detail** field on success:


```json
{
    "status" : "already treeparameter"
}

```


Here's an error respons:


```json
{
    "status" : "already treeparameter",
    "detail" : "event.raw.00"
}

```


Here the **detail** is used to indicate which parameter was involved in the error


## [/spectcl/parameter/create](#spectclparametercreate)


Creatse a new tree parameter in SpecTcl or an ordinary parameter in Rustogramer.  The parameter must not yet exist.


Note that with SpecTcl this is a front end to the `treeparameter -create`  command.


### [Query parameters](#query-parameters-3)


- **name** (Required string) - Name of the parameter to create.
- **low** (Required for SpecTcl optional for Rustogramer float) - parameter's low limit metadata.
- **high** (Required for SpecTcl optional for Rustogramer float) - parameter's high limit metadata.
- **units** (Optional string) - parameter's units of measure metadata (defaults to "" for SpecTcl)
- **description** (Optional Rustogramer only string) desription metadata for the parameter.


### [Reponse format detail](#reponse-format-detail-3)


Generic response where again, SpecTcl might omit the **detail** field on success.  THe **detail** filed is used on failure to supply additional information for the  failure reason.


#### [Sample Responses.](#sample-responses-3)


Successful creation:


```json
{
    "status" : "OK"
}

```


Failure in Spectcl:


```json
{
    "status" : "'treeparameter -create' failed: ",
    "detail" : "Could not parse  as type double\nUsage:\n     treeparameter -list ?pattern?\n     treeparameter -listnew\n     treeparameter -set name bins low high inc units\n     treeparameter -setinc name inc\n     treeparameter -setbins name bins\n     treeparameter -setunit name units\n     treeparameter -setlimits name low high\n     treeparameter -check name\n     treeparameter -uncheck name\n     treeparameter -create  name low high bins units\n     treeparameter -version"
}

```


Note how the **detail** field just contains the error message directly from the `treeparameter -create` command.


## [/spectcl/parameter/listnew](#spectclparameterlistnew)


### [Query parameters](#query-parameters-4)


None.


### [Reponse format detail](#reponse-format-detail-4)


**detail** is an array of names of parameters that wre created since the start of the run. Note that this is really only implemented in SpecTcl.  In Rustogramer, this will be an empty array.


#### [Sample Responses.](#sample-responses-4)


SpecTcl response:


```json
{
    "status" : "OK",
    "detail" : ["george"]
}

```


The parameter **george** was created.


## [/spectcl/parameter/check](#spectclparametercheck)


SpecTcl has a modification flag associated with each tree parameter.  The check flag is set if the parameter's metadta are modified.  This determines if that parameter has the check flag set.


### [Query parameters](#query-parameters-5)


- name (required string) - Name of the parameter to check on.


### [Reponse format detail](#reponse-format-detail-5)


- detail is an integer which is `0` if the check flag is not set and nonzero if it is.


#### [Sample Responses.](#sample-responses-5)


Found the parameter but its check flag is clear:


```json
{
    "status" : "OK",
    "detail" : 0
}

```


Nte that rustogramer will always have  a **detail** = 0.


No such parameter (SpecTcl)


```json
{
    "status" : "'treeparameter -check failed: ",
    "detail" : "Could not find parameter event.raw.000"
}

```


Note that in SpecTcl, **detail** is a string that describes why the request failed in detail. For Rustogramer, in case of failure, the **detail** string is `None`


## [/spectcl/parameter/uncheck](#spectclparameteruncheck)


Sets the check flag for a parameter to `0`.  This is implemented in Rustogramer but, unlike SpecTcl, has no effect


### [Query parameters](#query-parameters-6)


- **name** (Required string) - Name of the parameter to unceck.


### [Reponse format detail](#reponse-format-detail-6)


A generic response.  For SpecTcl, on success, this is only the **status** field, and the request never fails.  For Rustogramer; **detail** field is `null`


#### [Sample Responses.](#sample-responses-6)


Sample successful completion:


```json
{
    "status" : "OK",
    "detail" : null
}

```


## [/spectcl/parameter/version](#spectclparameterversion)


Reports the version of the tree paramter subsystem.


### [Query parameters](#query-parameters-7)


None


### [Reponse format detail](#reponse-format-detail-7)


Generic response with the stringified version number in the **detail** field


#### [Sample Responses.](#sample-responses-7)


```json
{ 
    "status" : "OK", 
    "detail" : "2.1" 
}

```




 Mobile navigation buttons 
[[**|chap7_2_responses]]
[[**|chap7_2_rawparameter]]



[[**|chap7_2_responses]]
[[**|chap7_2_rawparameter]]









 Custom JS scripts
