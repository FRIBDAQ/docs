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

# [/spectcl/project requests](#spectclproject-requests)


The `/spectcl/project` URI crates a new spectrum by projecting a 2-d spectrum (e.g.  `2` or `g2` ...) onto one of its axes.  Optionally the projection can be inside an area of interest specified by a contour.  The new spectrum can either be a snapshot spectrum, in which case it is never incremented after being created, or an ordinary spectcrum, in which case it will be incremented if possible.


Snapshot Spectra are handled differently betweeen SpecTcl and Rustogramer.  SpecTcl snapshot spectra are 1-d spectra that are wrapped in a container that prevents them from being incremented.  Rustogramer snapshot spectra are created by gating them on a `False` gate.  This also implies that a snapshot spectrum, in Rustogramer can be turned into an ordinary spectrum by ungating it, while a SpecTcl snapshot cannot.


## [/spectcl/snapshot](#spectclsnapshot)


### [Query parameters](#query-parameters)


- **source** (string)  - Mandatory name of the spectrum to project.
- **newname** (string) - Mandatory name of the new spectrom to create.
- **snapshot** (boolean) - Mandatory, if true a snapshot will be created. For SpecTcl any boolean Tcl value can be used.  For Rustogramer;
  - True values are any of `Yes`, `yes`, `True` or `true`
  - False values are any of `No`, `no`, `False` or `false`
- **direction** (string) - Mandatory direction selector indicating which direction the projectionis onto. One of:
  - Onto the X axis if `X` or `x`
  - Onto the Y axis if `Y` oe `y`
- **contour** (string) - Optional.  If supplied this must be a contour that is displayable on the spectrum and the projection will be inside the contour.  If the resulting spectrum is not a snapshot, it will be gated on the contour.  Thus if the contour is modified after the projection, the manner in which the spectrum is incremented will no longer be faithful to the original projection.
- **bind** (boolean) - Optional.  If supplied and `false` the new spectrum is not bound into display memory. If not supplied or `true` it is.


### [Response format detail](#response-format-detail)


A generic response is produced.


#### [Sample Responses.](#sample-responses)


Success (Rustogramer)


```json
{
    "status" : "OK",
    "detail" : ""
}

```


Failure from Rustogramer:


```json
{
    "status" : "Could not bind projected spectrum",
    "detail" : "<reason the projection failed>"
}

```


Failure from Spectcl


```json
{
    "status" : "'project' command failed: ",
    "detail" : "<error message from the project command>"
}

```




 Mobile navigation buttons 
[[chap7_2_pman]]
[[chap7_2_pseudo]]



[[chap7_2_pman]]
[[chap7_2_pseudo]]









 Custom JS scripts
