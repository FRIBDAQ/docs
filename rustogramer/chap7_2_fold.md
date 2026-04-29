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

# [/spectcl/fold requests](#spectclfold-requests)


The `/spectcl/fold` request domain creates and manipulates *folds*.  Folds are used in γ-ray spectroscopy to untangle decay chains.   SpecTcl and Rustogramer both support multiply-incremented spectrum types that are tailored for these sorts of experiments.


The Rustogramer mutiply-incremented 1-d/SpecTcl g1 spectrum can be used with an array of γ detectors; incremented for each γ ray detected by the array.  In decay cascades, if fully captured, each decay will increment the spectrum.   A decay chain will result in a set of correlated increments.


A fold is like a conditiont that, when applied to a  g1 spectrum, will increment all hits that are *not* in the condition.  Suppose, therefore, that you know the peak that corresponds to one of the decays in the sequential decay.  If you set a condition (slice) around that peak and apply that as a fold, and gate the spectrum on that condition as well, the spectrum will only show peaks that are in coincidence with the peak used to fold the spectrum.  These are the other decays in the sequential decay chain.


The following operations are defined on folds:


- [`/spectcl/fold/apply`](#spectclfoldapply) - Apply a condition as a fold to a spectrum
- [`/spectcl/fold/list`](#spectclfoldlist) - List the folds.
- [`/spectcl/fold/remove`](#spectclfoldremove) - Remove a fold.


## [/spectcl/fold/apply](#spectclfoldapply)


Apply a fold to a spectrum.  Note that folds can only be applied to an appropriate spectrum type.


### [Query parameters](#query-parameters)


- **gate** (string) - Mandatory name of the condition/gate to use as a fold.
- **spectrum** (string) - Mandatory name of the spectrum to fold with this gate.


### [Response format detail](#response-format-detail)


The response is a generic response.


#### [Sample Responses.](#sample-responses)


Success:


```json
{
    "status": "OK"
}

```


Failure (Spectcl):


```json
{
    "status": "'fold -apply' command failed",
    "detail": "<erorr message from fold -apply>"
}

```


Failure (Rustogramer):


```json
{
    "status": "Could not fold spectrum",
    "detail": "<why the fold failed>"
}

```


## [/spectcl/fold/list](#spectclfoldlist)


List the folds that are applied to spectra.


### [Query parameters](#query-parameters-1)


- **pattern** (string) - optional glob pattern to filter the listing to only spectra with names that match the pattern.  If omitted, the pattern defaults to `*` which matches all spectra.


### [Response format detail](#response-format-detail-1)


The **detail** is a vector of objects.  Each object has the following attributes:


- **spectrum** (string) - the name of a spectrum.
- **gate** (string) - the fold applied to the spectrum.


Note that the listing will only contain spectra that match the **pattern** and have a fold applied.


#### [Sample Responses.](#sample-responses-1)


Success with a spectrum named **gamma** folded on a condition named **peak** and no other folded spectra that match whatever the pattern was:


```json
{
    "status" : "OK",
    "detail" : [
        {
            "spectrum" : "gamma",
            "gate"     : "peak"
        }
    ]
}

```


## [/spectcl/fold/remove](#spectclfoldremove)


Removes a fold applied to a spectrum.


### [Query parameters](#query-parameters-2)


- **spectrum** (string) Mandatory name of the spetrum that will have folds removed.


### [Response format detail](#response-format-detail-2)


The response is a generic response


#### [Sample Responses.](#sample-responses-2)


Sucess:


```json
{
    "status": "OK"
}

```


Failure (SpecTcl)


```json
{
    "status" : "'fold -remove' command failed: ",
    "detail" : "<fold -removce error message>"
}

```


Failure (Rustogramer)


```json
{
    "status" : "Failed to remove fold",
    "detail" : <reason the fold could not be removed>"
}

```




 Mobile navigation buttons 
[[chap7_2_fit]]
[[chap7_2_integrate]]



[[chap7_2_fit]]
[[chap7_2_integrate]]









 Custom JS scripts
