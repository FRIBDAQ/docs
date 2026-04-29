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
[[chap7_2_responses]]
[[chap7_2_rawparameter]]



[[chap7_2_responses]]
[[chap7_2_rawparameter]]









 Custom JS scripts
