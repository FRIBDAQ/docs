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

# [/spectcl/psuedo requests](#spectclpsuedo-requests)


Psuedo parameters are a SpecTcl only object.  A SpecTcl psuedo parameter is a Tcl script that is invoked for each event and may return a new parameter value.  A pseudo parameter depends on a list of other parameters (some of which may also be psuedo parameters as long as they are defined chronogically before used).


Psuedo parameters are not terribly performant.  They are intended to answer what-if experiments which, if successful result in compiled code to produce the computed parameter.


Pseudo parameters are processed after all stages of the event processing pipeline have completed.


See the **psuedo** command documented in the [SpecTcl Command Reference](https://docs.nscl.msu.edu/daq/newsite/spectcl-5.0/cmdref/index.html) for more information on psuedo parameters.


The following URIs manipulate pseudo parameters:


- [`/spectcl/pseudo/create`](#spectclpseudocreate) - Create a new pseudo parameter.
- [`/spectcl/pseudo/list`](#spectclpseudolist) - List the properties of pseudo parameters.
- [`/spectcl/pseudo/delete`](#spectclpseudodelete) - Delete an exising pseudo parameter.


## [/spectcl/pseudo/create](#spectclpseudocreate)


### [Query parameters](#query-parameters)


- **pseudo** (string) - Mandatory name to give the pseudo parameter.  In addition to provide a name that is used to refer to the pseudo paramater, the actual **proc** name for the computation is derived from its name.
- **parameter** (string) - At least one instance is mandatory.  An instance of **parameter** should appear as a query parameter once for each parameter the computation depends on.
- **computation** (string) -Mandatory. The body of the computation.  You can assume that for each parameter specified by the **parameter** query parameter, there are a pair of variables available to the computation:
  - The name of the parameter (e.g. ?parameter=george implies a varialbe named `george`), will contain the value of the parameter for the event being processed when the pseudo code is invoked.
  - THe name of the parameter with `isValid` appended. THe example above implied, that a variable named `georgeisValid` is defined. This variable is `true` if the parameter has been produced by the proccessing pipline.


### [Response format detail](#response-format-detail)


The response is a generic response.


#### [Sample Responses.](#sample-responses)


Rustogramer


```json
{
    "status" : "Pseudo parameters are not implemented",
    "detail" : "This is not SpecTcl"
}

```


SpecTcl success:


```json
{
    "status": "OK"
}

```


SpecTcl failure:


```json
{
    "status": "'pseudo' command failed",
    "detail": "<Error message fromt he pseudo command"
}

```


## [/spectcl/pseudo/list](#spectclpseudolist)


List pseudo parameters and their properties.


### [Query parameters](#query-parameters-1)


- **pattern** (string) - Optional parameter.  If provided, the names of pseudos included inthe listing must match the pattern.  If not supplied, the pattern defaults to ```*```` which matches everything.


### [Response format detail](#response-format-detail-1)


**detail* is an array containing objects, on object for each listed pseudo parameter.  The attributes of the objects are:


- **name** (string) - name of the pseudo parameter.
- **parameters** (array of strings) - the parameters the pseudo parameter computation depends on.
- **computation** (string) - The computation script.


#### [Sample Responses.](#sample-responses-1)


From Rustogramer:


```json
{
    "status": "Psuedo parameters are not implemented - this is not SpecTcl",
    "detail": []
}

```


Successful SpecTcl with a parameter `add12` that add par1 and par2 together.


```json
{
    "status" :"OK",
    "detail": [
        {
            "name" : "add12",
            "parameters": [
                "par1", 
                "par2"
            ],
            "computation" : " if {$par1isValid && $par2isValid} {
                return [expr {$par1 + $par2}]
            } else {
                return -1000
            }
            "
        }
    ]
}

```


SpecTcl failure:


```json
{
    "status" : "'pseudo -list' command failed",
    "detail" : "<error message from pseudo -list command"
}

```


## [/spectcl/pseudo/delete](#spectclpseudodelete)


Deletes an existing Psuedo parameters.


### [Query parameters](#query-parameters-2)


- **name** - Name of the parameter to delete.


### [Response format detail](#response-format-detail-2)


Response is a Generic Response.


#### [Sample Responses.](#sample-responses-2)


Rustogramer:


```json
{
    "status" :"Pseudo parameters are not implemented",
    "detail" : "This is not SpecTcl"
}

```


SpecTcl success:


```json
{
    "status" : "OK"
}

```


SpecTcl failed:


```json
{
    "status" : "'pseudo -delete' command failed",
    "detail" : "<error message from pseudo -delete command"
}

```




 Mobile navigation buttons 
[[chap7_2_project]]
[[chap7_2_roottree]]



[[chap7_2_project]]
[[chap7_2_roottree]]









 Custom JS scripts
