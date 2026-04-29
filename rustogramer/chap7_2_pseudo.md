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
[[**|chap7_2_project]]
[[**|chap7_2_roottree]]



[[**|chap7_2_project]]
[[**|chap7_2_roottree]]









 Custom JS scripts
