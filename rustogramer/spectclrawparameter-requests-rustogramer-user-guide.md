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

# [/spectcl/rawparameter requests](#spectclrawparameter-requests)


For Rustogramer, the requests in this URI domain map to similar requests in the
[[./chap7_2_parameter]] domain.  For SpecTcl, however for historical reasons, there is a difference between a raw parameter and a tree parameter.


Originally tree parameters were  a contributed package written by Daniel Bazin.  Later, due to its utility, tree parameters were incorporated into supported SpecTcl code.  However a distinction does exist, internally between tree parameters and the original raw parameters, which may not be mapped to tree paramters.


In SpecTcl, therefor, these URIs manipulate raw parameters without affecting any tree parameters that might be bound to them.


The requests include:


- [`/spectcl/rawparameter/new`](#spectclrawparameternew) (Rustogramer maps this to [[./chap7_2_parameter#spectclparametercreate]]).  SpecTcl creates a new raw parameter.
- [`/spectcl/rawparameter/delete`](#spectclrawparameterdelete) (Rustogramer implements this).  This deletes an existing (raw) parameter.
- [`/spectcl/rawparameter/list`](#spectclrawparameterlist) (Rustogramer maps this to [[./chap7_2_parameter#spectclparameterlist]])


## [/spectcl/rawparameter/new](#spectclrawparameternew)


Creates a new raw parameter.  Note that in Rustogramer, this is forwarded to the handler for [[./chap7_2_parameter#spectclparametercreate]]. Refer to that documentation.  This section documents how this URI is implemented for SpecTcl.


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
[[chap7_2_parameter]]
[[chap7_2_gates]]



[[chap7_2_parameter]]
[[chap7_2_gates]]









 Custom JS scripts
