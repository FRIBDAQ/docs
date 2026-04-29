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

# [/spectcl/specstats requests](#spectclspecstats-requests)


Returns statistics about the underflows and overflows for spectra.


## [/spectcl/specstats](#spectclspecstats)


### [Query parameters](#query-parameters)


- **pattern** (string) - Optional pattern.  Only spectra whose names match the glob pattern are included in the listing.  The pattern defaults to `*` matching all names if not provided in the request.


### [Response format detail](#response-format-detail)


**detail** is an array of structs, one for each spectrum that matches the pattern.  Each struct has the following attributes:


- **name** (string) name of the spectrum.
- **undeflows** (array of u32) - two element array of number of underflows.  The first element are X axis overflows the second, Y axis overflows.
- **overflows** (array of u32) - two element array of number of underflows.  The first element are X axis overflows the second, Y axis overflows.


Note that SpecTcl, for one dimensional spectrim types will have a one element array for both **underflows** and **overflows** rustogramer will unconditionally use 2 element arrays but the second element of the array should be ignored for one dimensional spectrum types.


#### [Sample Responses.](#sample-responses)


Rustogramer  a single 1-d spectrum matches:


```json
{
    "status" : "OK", 
    "detail" : [
        {
            "name" : "1-d-spectrum",
            "underflows" : [12, 0],
            "overflows":   [732, 0]
        }
    ]
}

```


Same result for SpecTcl:


```json
{
    "status" : "OK", 
    "detail" : [
        {
            "name" : "1-d-spectrum",
            "underflows" : [12],
            "overflows":   [732]
        }
    ]
}

```


Both Rustogramer an SpecTcl 2-d spectrum matches:


```json
{
    "status" : "OK", 
    "detail" : [
        {
            "name" : "2-d-spectrum",
            "underflows" : [12, 5],
            "overflows":   [732, 0]
        }
    ]
}

```




 Mobile navigation buttons 
[[chap7_2_ringformat]]
[[chap7_2_swrite]]



[[chap7_2_ringformat]]
[[chap7_2_swrite]]









 Custom JS scripts
