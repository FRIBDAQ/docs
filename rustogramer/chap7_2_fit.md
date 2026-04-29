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
[[**|chap7_2_filter]]
[[**|chap7_2_fold]]



[[**|chap7_2_filter]]
[[**|chap7_2_fold]]









 Custom JS scripts
