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

# [/spectcl/rootree requests](#spectclrootree-requests)


This URI domain is only available in SpecTcl.  It supports access to SpecTcl's ability to make root trees from the parameters created by  its event processing pipeline.   Since Rustogramer does not create root trees, this is not meaningful and making requests to these URIs for Rustogramer will result in a Generic response of the form:


```json
{
    "status": "Root Tree output is not supported",
    "detail": "This is not SpecTcl"
}

```


unless otherwise noted (e.g. for reponses from SpecTcl that are not generic responses).


SpecTcl, supports the following URIs:


- [`/spectcl/roottree/create`](#spectclroottreecreate) - Makes a new root tree.
- [`/spectcl/roottree/delete`](#spectclroottreedelete) - Delete an existing root tree.
- [`/spectcl/roottree/list`](#spectclroottreelist) - List root trees and their properties.


For more information about root tree support in SpecTcl, see the `roottree` command in the
[SpecTcl Command Reference](https://docs.nscl.msu.edu/daq/newsite/spectcl-5.0/cmdref/index.html).


## [/spectcl/roottree/create](#spectclroottreecreate)


Create a new root tree object.


### [Query parameters](#query-parameters)


- **name** (string) - Required. Name of the new tree being created.  Must be unique.
- **parameter** (string) - At least one required. Each instance of the **parameter** query paramater provides a glob pattern.  Parameters in the event which match the pattern are included in the output tree.
- **gate** (string) - Optional.  If provided the root tree will only output events that satisfy the specified gate.  Note that:
  - If no gate is specified all events are written.
  - Changes to the gate dynamically affect the roottree output.
  - The point above means that if you delete the gate, the root tree will not output events as in SpecTcl a deleted gate is the same as a `False` gate.


### [Response format detail](#response-format-detail)


**detail** is a generic response.


#### [Sample Responses.](#sample-responses)


Success:


```json
{
    "status" : "OK"
}

```


Failure:


```json
{
    "status" : "'roottree create' command failed",
    "detail":  "<root tree create error message>"
}

```


## [/spectcl/roottree/delete](#spectclroottreedelete)


Delete an existing root tree object.


### [Query parameters](#query-parameters-1)


- **tree** (string) - Required.  The name of the tree to delete.


### [Response format detail](#response-format-detail-1)


The response is a generic response.


#### [Sample Responses.](#sample-responses-1)


Success:


```json
{
    "status": "OK"
}

```


Failure:


```json
{
    "status" : "'roottree delete' command failed",
    "detail" : "<error message from roottree delete command>"
}

```


## [/spectcl/roottree/list](#spectclroottreelist)


Lists the properties of root trees.


### [Query parameters](#query-parameters-2)


- **Pattern** (string) - Optional. If provided, only the root trees with names that match the glob pattern are included in the list.  If not provided, the pattern defaults to `*` which matches all names.


### [Response format detail](#response-format-detail-2)


**detail** is an array of objects.  Each object describes one root tree and has the following attributes:


- **tree** (string) - name of the tree.
- **params** (array of strings) - Array of parameter patterns that are booked into the tree.
- **gate** (string) - name of the tree's gate.  If the tree does not have a gate, this will be an empty string.


#### [Sample Responses.](#sample-responses-2)


Since the **detail** is not a string, the Rustogramer return object looks like this:


```json
{
    "status" : "Root tree output is not implemented - this is not SpecTcl",
    "detail" : []
}

```


This shape is compatible with what's expected by SpecTcl clients.


SpecTcl success with one matching tree:


```json
{
    "status" : "OK", 
    "detail" :[
        {
            "tree" : "atree",
            "params": [
                "event.raw.*",
                "event.sum"
            ],
            "gate": "tree-gate"
        }
    ]
}

```


SpecTcl failure is a generic response:


```json
{
    "status" : "'roottree list' command failed",
    "detail" : "<roottree list error message>"
}

```




 Mobile navigation buttons 
[[chap7_2_pseudo]]
[[chap7_2_script]]



[[chap7_2_pseudo]]
[[chap7_2_script]]









 Custom JS scripts
