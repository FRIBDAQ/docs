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
[[chap7_2_fold]]
[[chap7_2_shmem]]



[[chap7_2_fold]]
[[chap7_2_shmem]]









 Custom JS scripts
