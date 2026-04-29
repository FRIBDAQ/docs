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

# [/spectcl/treevariable requests](#spectcltreevariable-requests)


This is only supported by SpecTcl, as Rustogramer does not support tree variables.


Almost all requests directed at Rustogramer for this domain produce Generic Responses that are:


```json
{
    "status" :"Tree variables are not implemented",
    "detail" : "This is not SpecTcl"
}

```


Other return types are noted in the individual request documentation.


The domain provides the following URIs.


- [`/spectcl/treevariable/list`](#spectcltreevariablelist) - List tree variables and their properties.
- [`/spectcl/treevariable/set`](#spectcltreevariableset) - Set new value and units for a tree variable.
- [`/spectcl/treevariable/check`](#spectcltreevariablecheck) - See if the changed flag is set for the tree variable.
- [`/spectcl/treevariable/setchanged`](#spectcltreevariablesetchanged) - Set the changed flag for a treevariable.
- [`/spectcl/treevariable/firetraces`](#spectcltreevariablefiretraces) - Fire the traces for a set of tree variables, allowin scripts and UI elements that care about the variable to know about changes.


In SpecTcl, tree variables are bound to Tcl variables as linked variables.  the set operation changes the value of the linked variable.  In general, for scripts which have traces set o the variable, traces must be explicitly fired (`/spectcl/treevariablefiretraces`) for those traces to execute.  Tk GUi elements that bind to variables will, behind the scenes, establish traces and therefore traces must be fired for those elements to update visually.  The units metadata are kept separate from the Tcl interpreter and is only known to it through the `treevariable -list` command.


The purpose of the changed flag is to keep track of which variables have values different from those compiled into SpecTcl.  This allows software that saves the SpecTcl state to selectively save only the changed treevariables.


## [/spectcl/treevariable/list](#spectcltreevariablelist)


Lists the priperties of all treevariables.  Note that there is no way to selectively list the treevariables (e.g. with a pattern query parameter.)


### [Query parameters](#query-parameters)


None supported.


### [Response format detail](#response-format-detail)


The **detail** is an array of objects.  Each object describes  tree variable and has the following attributes.


- **name** (string) - name of the tree variable being described.
- **value** (float) - Value of the variable.  This will be correct whether traces have been fired or not.
- **units** (string) - Units of measure metadata.


#### [Sample Responses.](#sample-responses)


To maintain the shape of the response detail Rustogramer's response is:


```json
{
    "status" : "Tree variables are not implemented.  This is not SpecTcl",
    "detail" : []
}

```


Here's a SpecTcl return with one treevariable:


```json
{
    "status" : "OK",
    "detail" : [
        {
            "name" : "avarialbe",
            "value" : 3.14159265359,
            "units" : "radians/half-pie"
        }
    ]
}

```


Failure (I'm not sure I see how this can ever happen but...):


```json
{
    "status" :  "'treevariable -list' failed: ",
    "detail" : "<error message from treevariable -list>"
}

```


## [/spectcl/treevariable/set](#spectcltreevariableset)


Sets the value and units of measure metadata of a treevariable.  Note that for historical reasons, both must be set.


### [Query parameters](#query-parameters-1)


- **name** (string) - Required. Name of the treevariable to modify.
- **value** (float) - Required.  New value for the tree variable.
- **units** (string) - Required.  New units of measure for the variable.


### [Response format detail](#response-format-detail-1)


Generic response.


#### [Sample Responses.](#sample-responses-1)


Success:


```json
{
    "status" : "OK"
}

```


Failure:


```json
{
    "status" : "'treevariable -set' failed",
    "detail" : "<treevariable -set error message"
}

```


## [/spectcl/treevariable/check](#spectcltreevariablecheck)


Return the value of the check flag for a tree variable.  The check flag is non-zero if, at any time during the SpecTcl run, the treevariable was modified.


### [Query parameters](#query-parameters-2)


- **name** (string) - Required. Name of the tree variable being queried.


### [Response format detail](#response-format-detail-2)


On success, **detail** containss an integer that is zero if the change flag was not set and non-zero if it was.


#### [Sample Responses.](#sample-responses-2)


Change flag not set:


```json
{
    "status" : "OK"
    "detail" : 0
}

```


Error:


```json
{
    "status" : "'treevariable -check' failed",
    "detail" : "<treevariable -check error message>"
}

```


Note: Prior to 5.13-012, the error return mistakenly had a **status** of `OK`


## [/spectcl/treevariable/setchanged](#spectcltreevariablesetchanged)


Set a treevariable changed flag.  The changed flag is a latched boolean that is initialized `false` but is set to `true` by, e.g. this request, when a value is changed.


### [Query parameters](#query-parameters-3)


- **name** (string) -  Required. Name of the treevariable whose changed flag will be set.


### [Response format detail](#response-format-detail-3)


Generic response.


#### [Sample Responses.](#sample-responses-3)


Success:


```json
{
    "status"  : " OK"
}

```


Failure:


```json
{
    "status" :  "'treevariable -setchanged' command failed",
    "detail" : "<treevariable -setchanged' error message" 
}

```


Note: Prior to 5.13-012, the error return mistakenly had a **status** of `OK`


## [/spectcl/treevariable/firetraces](#spectcltreevariablefiretraces)


Fire traces associated with a set of tree variable.s


### [Query parameters](#query-parameters-4)


- **pattern** (string) - Optional. The traces associated with all treevariables with names matching the pattern are fired.  If the pattern is omitted, `*` is matched, which matches everything.


### [Response format detail](#response-format-detail-4)


Generic response


#### [Sample Responses.](#sample-responses-4)


Success:


```json
{
    "status" : "OK"
}

```


Failure:


```json
{ 
    "status" : "'treevariable -firetraces failed: ", 
    "detail" : "treevariable -firetraces error message> "
}

```




 Mobile navigation buttons 
[[chap7_2_script]]
[[chap7_2_version]]



[[chap7_2_script]]
[[chap7_2_version]]









 Custom JS scripts
