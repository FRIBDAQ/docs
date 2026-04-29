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
[[**|chap7_2_script]]
[[**|chap7_2_version]]



[[**|chap7_2_script]]
[[**|chap7_2_version]]









 Custom JS scripts
