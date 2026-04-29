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

# [/spectcl/gate requests](#spectclgate-requests)


The /spectcl/gate domain or URIs provides the ability to manipulate gates (rustogramer conditions).


URIs include:


- [`/spectcl/gate/list`](#spectclgatelist) - lists defined conditions.
- [`/spectcl/gate/delete`](#spectclgatedelete) - Delets a condition
- [`/spectcl/gate/edit`](#spectclgateedit) - Create or modify a condition.


## [/spectcl/gate/list](#spectclgatelist)


Returns a list of gates with names that match an optional pattern.


### [Query parameters](#query-parameters)


- **pattern** (optional string) If not supplied this defaults to `*` which matches all names.  The pattern can use any filesystem wild-card characters and patterns.


### [Response format detail](#response-format-detail)


The **detail** of the response is a bit complex.   It consists of an array of structs.  Some struct fields are gate type dependent and, for SpecTcl unecessary fields are not present while for rustogramer all fields are present but the unecessary fields have the value `null`


Each struct has the following fields.


- **name** (String) - Always present.  This is the name of the condition/gate
- **type** (String) - Always present.  The gate type string. See the [SpecTcl command reference for `gate`](https://docs.nscl.msu.edu/daq/newsite/spectcl-5.0/cmdref/index.html) for the possible values  and meanings of this string.
- **gates** (Array of Strings) - Present only for compound conditions/gates (e.g. *and* *or* an d *not*).
- **parameters** (Array of Strings) - Present only for conditions/gates that depend on parameters (for example, and not limitied to *slice* or *contour*).  This is a list of the parameter names the condition/gate depends on.
- **points** (Array of Point structs ) - Present only for  conditions/gates that represent geometric shapes in two dimensional parameter space (for example, but not limited to *slice* or *contour*).  These are the points that make up the shape.  Each point, itself, is a struct made up of.
  - **x** - (float) the x coordinate of the point.
  - **y** - (float) the y coordinate of the point.
- **low** - (float) Present only for conditions/gates that are a one-dimensional slice in parameter space.  This is the low limit of that slice.
- **high** - (float) Present only for conditions/gates that are a one-dimensional slice in parameter space.  This is the high limit of that slice.


#### [Sample Responses.](#sample-responses)


Here is a response that shows pretty much all of the gate struct types (from SpecTcl so unused fields are omitted - had this come from Rustogramer, unused fields would be `null`):


```json
{
    "status" : "OK",
    "detail" : [{
        "name"       : "acontour",
        "type"       : "c",
        "parameters" : ["event.raw.00","event.raw.01"],
        "points"     : [{
            "x" : 398.316437,
            "y" : 458.697357
        },{
            "x" : 206.994919,
            "y" : 138.077942
        },{
            "x" : 647.967651,
            "y" : 77.811142
        },{
            "x" : 845.511047,
            "y" : 302.003662
        },{
            "x" : 710.186035,
            "y" : 550.302917
        }]
    },{
        "name"  : "anand",
        "type"  : "*",
        "gates" : ["acontour","anot"]
    },{
        "name"  : "anot",
        "type"  : "-",
        "gates" : ["aslice"]
    },{
        "name"       : "aslice",
        "type"       : "s",
        "parameters" : ["event.raw.00"],
        "low"        : 330.595703,
        "high"       : 674.400635
    }]
}

```


- `acontour` is a contour and therefore has **points**.  Note that the points are in parameter space defined by X=`event.raw.00` and Y=`event.raw.01`
- `aslice`  is a slice gate and therefore has **low** and **high**
- `anot` is a not gate and therefore has **gates** with a single gate name, the name of the gate it negates.
- `anand` is an And gate which also has ***gates***, in this case both `acontour` and `anot` must be true (the inverse of `aslice`) for the condition to be true.


Another important note;  The order in which the conditions are listed should not be assumed.  While SpecTcl will, in general list the conditions alphabetically by name, Rustogramer will list them at random.  In particular this means that, in order to reconstruct the gates, they must be re-ordered in dependency order (you can't make `anand` until `acontour`  and `anot` have been defined and you can't make `anot` until `aslice` is defined).


## [/spectcl/gate/delete](#spectclgatedelete)


Deletes a condition.  Note  that while rustogramer actually delete conditions, SpecTcl modifies them into False conditions.


### [Query parameters](#query-parameters-1)


- **name** (String) this mandatory parameter is the name of the condition to delete.


### [Response format detail](#response-format-detail-1)


A generic response.


#### [Sample Responses.](#sample-responses-1)


Successful condition deletion:


```json
{
    "status" : "OK"
}


```


Where Rustogramer's response will include an empty **detail** field.
Note that since SpecTcl just replaces deleted gates with a False gate it is legal to delete a "deleted" gate.  That is an error in Rustogramer, however.


Attempting to delete a nonexistent gate `anando` generates the following in SPecTcl


```json
{
    "status" : "not found",
    "detail" : "anando"
}

```


In rustogramer you'll get:


```json
{
    "status" : "Failed to delete condition anando",
    "detail" : "anando"
}

```


## [/spectcl/gate/edit](#spectclgateedit)


Creates a new condition/gate or edits an existing one.  These two operations are functionalyly identical.  If the condition specified in the query parameters for this request already exists, it is replaced.  If not, it is created.


Note that condition replacement is dynamic.  Spectra that gave this condition applied to them as gates have their gating modified to reflect the new condition definition on the next event processed.


### [Query parameters](#query-parameters-2)


- **name** (String) - Mandatory specifies the name of the condition/gate being edited.
- **type** (String) - mandatory specifies the type of condition/gate being edited.  See the [SpecTcl command reference for `gate`](https://docs.nscl.msu.edu/daq/newsite/spectcl-5.0/cmdref/index.html) for the possible values  and meanings of this string.
- **gate** (Multiple String) - This is required for conditions that depend on other conditions.  It should be presenet once for each dependent condition. For example:  
  `.../spectcl/gate/edit?name=anand&type=*&gate=g1&gate=g2&gate=g3`  
  is how to specify an and gate named `anand` that depends on the gates `g1`, `g2` and `g3`
- **xparameter** (String) - Mandatory for two dimensional geometric shape gates in parameter space. The parameter on the X axis of the condition/gates space.
- **yparameter** (String) - Mandatory for two dimensional geometric shape gates in parameter space. The parameter on the Y axis of the condition/gates space.
- **parameter** (String) - Mandaatory for slice (`s` type) and for conditions with multiple unorderd parameters, for example gamma slices (`gs`) or gamma contours (`gc`).  This can be specified as many times as needed to supply all parameters. For examle the gamma contour depending on p1, p2, p3 would be something like:<br'>
  `.../spectdl/gate/edit?name=gamma-contour&type=gc&parameter=p1&parameter=p2&parameter=p3...`
- **xcoord** (float) - mandatory for 2d geometric gates (e.g. contours `c`).  This is the X-coordinate of a gate point.   specify this as many times as needed.  To specify an ordered set of x-coordinates.
- **ycoord** (float) - mandatory for 2d geometric gates (e.g. contours `c`).  This is the X-coordinate of a gate point.   specify this as many times as needed.  To specify an ordered set of x-coordinates.  Here, for example, is a definition of a contour that is a right triangle:


```
.../spectcl/gate/edit?name=contour&type=c&xparameter=p1&yparameter=p2&xcoord=100&ycoord=100&xcoord=200&ycoord=100&xcoord=200&ycoord=200

```


- **low** (float) - mandatory for slice like gates (e.g. ``s`and`gs```); The  low limit of the condition.
- **high** (float) - mandatory for slice like gates; the high limit of the conditions.
- **value** (integer) - For SpecTcl mask gates, this is the mask value.


### [Response format detail](#response-format-detail-2)


The response is a generic response.


#### [Sample Responses.](#sample-responses-2)


Successful gate creation in SpecTcl:


```json
{
    "status" : "OK"
}

```


Rustogramer will include an empty **detail** field as well.


Failed gate creation - **type** parameter omitted (SpecTcl):


```json
{
    "status" : "missing Parameter",
    "detail" : "type"
}

```


Note that the REST server in Rustogramer does some pre-processing and will fail to match a URI that does not include both a **name** and a **type**


However detailed error messages will be in the **status** field for rustogramer.  Suppose, for example, you try to create a not codition without supplying a dependent gate:


```json
{
    "status" : "Not conditions can have at most one dependent condition",
    "detail" : ""
}

```


Will be returned.




 Mobile navigation buttons 
[[**|chap7_2_rawparameter]]
[[**|chap7_2_spectrum]]



[[**|chap7_2_rawparameter]]
[[**|chap7_2_spectrum]]









 Custom JS scripts
