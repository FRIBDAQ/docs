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

# [/spectcl/integrate requests](#spectclintegrate-requests)


This request allows you to integrate regions of interest on 1-d or 2-d spectra.


## [/spectcl/integrate](#spectclintegrate)


Request the integraion. The region of interest can be specfied:


- 1-d spectrum :
  - as a low/high pair of floats.
  - as a slice condition.
- 2-d spectrum :
  - As a set of x/y points that are closed to form a contour-like area of interest (insidedness is computed in the same way as it is for contours).
  - As a contour condition/gate.


### [Query parameters](#query-parameters)


At least one set of the optional parameters that specify a region of interest must be present in the query parameters.


- **spectrum** (string) - Required - name of the spectrum to integrate.
- **gate** (string) - Optional Name of gate whose interior is integrated.
- For 1-d spectra only providing explicit limits:
  - **low** (float) - Low limit of region of interest.
  - **high** (float) - High limit of region of interest.
- For 2-d spectra only, providing an explicit ROI
  - **xcoord** (float) - X coordinates of points that define the ROI.
  - **ycoord** (float) - Y Coordinates of points that define the ROI.


Note that **xcoord** and **ycoord** must appear at least three times to define an area of interest.  These paramters are taken as defining an ordered set of coordinats so, for example:


```
...?xcoord=100&xcoord=200&xcoord=200&ycoord=100&ycoord=100&ycoord=150....

```


Defines the region of interest as a triangle with coordinates:


```
(100,100)
(200,100)
(200,150)

```


### [Response format detail](#response-format-detail)


The **detail** of the response provides the integration details.  Note there are slight differencess betwen SpecTcl and rustogramer;  The attributes of the object are:


- **centroid**  - Centroid of the integration.  For SpecTcl; integrating a 1d, this is a scaler, or a 2 element array if a 2d.  For rustogramer, this is always an array with one element for a 1-d spectrum and two elements for a 2-d.
- **fwhm** - Full width at half maximum under gaussian shape assumptions.  SpecTcl may be a scalar float or 2 element float array; while rustogramer is a one or two element array of floats.  Same as for **centroid** above.
- **counts** (unsigned integer) - total counts inside the AOI.


#### [Sample Responses.](#sample-responses)


SpecTcl 1-d success.


```json
{
    "status" : "OK",
    "detail" {
        "centroid" : 102.512,
        "fwhm" : 5.32,
        "counts": : 124567

    }
}

```


Rustogramer 1-d success.


```json
{
    "status" : "OK",
    "detail" {
        "centroid" :[102.512],
        "fwhm" : [5.32],
        "counts": : 124567

    }
}

```


2-d success.


```json
{
    "status" : "OK",
    "detail" {
        "centroid" :[102.512, 50.7],
        "fwhm" : [5.32, 7.66],
        "counts": : 124567

    }
}

Failure (SpecTcl)

Below, the word ```$command``` is the ```integrate``` command the REST handler generated:

```json
{
    "status": "'$command' failed",
    "detail":  "<reason for the failure>"
}

```


Failure (Rustogramer) - only either **low** or **high** were provided as query parameters:


```json
{
    "status": "If using limits both low and high must be provided"
    "detail" :
    "detail" {
        "centroid" :[0.0],
        "fwhm" : [0.0],
        "counts": : 0

    }
}

```




 Mobile navigation buttons 
[[**|chap7_2_fold]]
[[**|chap7_2_shmem]]



[[**|chap7_2_fold]]
[[**|chap7_2_shmem]]









 Custom JS scripts
