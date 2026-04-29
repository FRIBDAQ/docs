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

# [/spectcl/fit requests](#spectclfit-requests)


This is only avaialble with SpecTcl.  SpecTcl supports fitting regions of interest on 1-d spectra.  The actual fit function used can be extended, however `linear` and `gaussian`.  Note that `gaussian` performs a gaussian fit on a constant background.


See the [SpecTcl command reference](https://docs.nscl.msu.edu/daq/newsite/spectcl-5.0/cmdref/index.html) for information about the `fit` command.  The set of fits is extensible by the user.  See the section "Extending the set of SpecTcl fit types in the [SpecTcl programming guide](https://docs.nscl.msu.edu/daq/newsite/spectcl-5.0/pgmguide/index.html)


The `/spectcl/fit` domain of URIs provides the following operations:


- [`/spectcl/fit/create`](#spectclfitcreate) - create a new SpecTcl fit object.
- [`/spectcl/fit/update`](#spectclfitupdate) - Computes fit parameter values on current histogram data.
- [`/spectcl/fit/delete`](#spectclfitdelete) - Delete a spectcl fit object.
- [`/spectcl/fit/list`](#spectclfitlist) - List one or more fits providing each fit's current function parameterization.
- [`/spectcl/fit/proc`](#specclfitproc) - Returns a Tcl proc that can be used to evaluate the fit at any point.


## [/spectcl/fit/create](#spectclfitcreate)


Creates a new fit object. Fit object, once created, can be updated, which causes them to compute/recompute their parameterizations, which can the be fetched via the list operation.


### [Query parameters](#query-parameters)


- **name** (string) - mandatory name to associate with the fit object.
- **spectrum** (string) - mandatory name of a spectrum that only has an X paramter axis (e.g. a 1d or gamma 1d spectrum).
- **low** (unsigned integer) - mandatory low limit in channels of the region of interest.
- **high** (unsigned integer) - mandatory high limit in channels of the region of interest.
- **type** (string)  - Fit type string, e.g. `gaussian`


### [Response format detail](#response-format-detail)


The response is a Generic response.


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
    "status" : "'fit'command failed: ",
    "detail" : "<error message from the fit command>"
}

```


## [/spectcl/fit/update](#spectclfitupdate)


Performs fits an updates the paramterization of the fit functionss stored in the update.  This computes the parameterization of the fit functions on current data.  Prior to its first update, the parameterization is whatever values the author of that fit type chose and, in general, is not meaningful.


### [Query parameters](#query-parameters-1)


- **pattern** (string) - Glob pattern.  Only fits with names that match the pattern are pdated.


### [Response format detail](#response-format-detail-1)


Response is a generic response.


#### [Sample Responses.](#sample-responses-1)


On Success:


```json
{
    "status" : "OK"
}

```


On Failure:


```json
 {
    "status": "'fit'command failed: ",
    "detail": "<Error message from the fit command>"

 }

## /spectcl/fit/delete

Deletes a single named fit object.

### Query parameters

* **name** - name of the fit to delete.

### Response format detail

The response is a generic response.

#### Sample Responses.

On Success:

```json
{
    "status" : "OK"
}

```


On Failure:


```json
{
    "status" : "'fit'command failed: ",
    "detail" : "<Error returned from the fit command>"
}

```


## [/spectcl/fit/list](#spectclfitlist)


Lists a set of fits.  When fits are listed the fit function parameters as of the most recent `/update` are also listed.


### [Query parameters](#query-parameters-2)


- **pattern** (string) - (optional)  Restricts the listed fits to only those that match the glob pattern provided.


### [Response format detail](#response-format-detail-2)


The **detail** is an array of objects.  Each object describes a fit that was done and contains the fields:


- **name** (string) - Name of the fit being described.
- **spectrum** (string) name of the spectrum the fit is defined on
- **type** (string) - fit type (e.g. `gaussian`).
- **low** (unsigned) - Low bin of the area of interest.
- **high** (unsigned) - High bin of the area of interest.
- **parameters** (Object) - the shape of this object depends on the type of fit.  Fields of this object are the most recently computed fit parameters.  See the `fit` command in the [SpecTcl command reference](https://docs.nscl.msu.edu/daq/newsite/spectcl-5.0/cmdref/index.html) for the fields for each of the built-int fit types.  The fields provided by user written fits depend on the author of the fit type support.  All fit types *should* provide a **chisquare** field which holds the goodness of fit.


#### [Sample Responses.](#sample-responses-2)


Successful list where a single gaussian fit is matched to **pattern**:


```json
{
    "status" : "OK",
    "detail" : [
        {
            "name" : "agaussianfit",
            "spectrum" : "aspectrum",
            "type" : "gaussian",
            "low" : 100,
            "high" : 300,
            "parameters" :  {
               "baseline" : 127,
               "height"   : 1234.7,
               "centroid" : 207.6,
               "sigma"    : 12.7,
               "chisquare" : 15.766
            }
        }
    ]
}

```


Note the `parameters` are just pulled out of the air and do not relflect any actual fit.


## [spectcl/fit/proc](#spectclfitproc)


Given a fit, provides a Tcl proc that can be given channel numbers (floating point) and return to value of the fit at that channel.


### [Query parameters](#query-parameters-3)


- **name** - name of the fit.


### [Response format detail](#response-format-detail-3)


A generic response is produced however **detail** is the text of a Tcl proc.


#### [Sample Responses.](#sample-responses-3)


Suppose we have a linear fit, what you might get back is:


```json
{
    "status" : "OK",
    "detail" : "proc fitline x {   \nset slope 2.7\nset offset 362.6\nreturn [expr {$x*$slope+$offset}]\n}"
}

```




 Mobile navigation buttons 
[[chap7_2_filter]]
[[chap7_2_fold]]



[[chap7_2_filter]]
[[chap7_2_fold]]









 Custom JS scripts
