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

# [/spectcl/attach](#spectclattach)


This set of URIs manipulates the attachment of a data source to the server.  The following URIs are provided:


- [`/spectcl/attach/attach`](#spectclattachattach) attaches a data source to the server. Note that any previously attached source is detached.
- [`/spectcl/attach/list`](#spectclattachlist) describes the data source attached tot he server.
- [`/spectcl/attach/detach`](#spectclattachdetach) detaches the current data source.


## [/spectcl/attach/attach](#spectclattachattach)


Attaches a new data source to the server.  The server detaches any previously attached data source.


### [Query parameters](#query-parameters)


- **type**  Type of data source to attach.  This can be one of:
  - `pipe` (only supported by SpecTcl) data comes from a program started on the other end of a pipe.  The program must emit data to `stdout`
  - `file` (supported by both)  data is read from a file.
- **source** Specifies the data source.  This depends on the data source type:
  - `pipe` A string containing the program and its arguments.  For example suppose you are attaching gzcat to uncompress a file named ./events.gz  this would be `gzcat ./events.gz`
  - `file` Path to the file to attach e.g. `./run-0000-00.evt`
- **size** optional size of reads done from the data source.  This defaults to `8192` if not provided.   Rustogramer ignores this but SpecTcl honors it.


### [Response format detail](#response-format-detail)


A Generic response is returned.


#### [Sample Responses.](#sample-responses)


Success:


```json
{
    "status" : "OK",
    "detail" : ""
    
}

```


Failure:


```json
{
    "status" : "attach command failed",
    "detail" : "No such file or directory"
}

```


## [/spectcl/attach/list](#spectclattachlist)


Queries what is attached to the server.


### [Query parameters](#query-parameters-1)


No query parameters are supported/required


### [Response format detail](#response-format-detail-1)


A generic repsonse.  This always has **status**=`OK`


#### [Sample Responses.](#sample-responses-1)


Attached to a file:


```json
{
    "status" : "OK",
    "detail" : "File: run-0001-00.evt"
}

```


## [/spectcl/attach/detach](#spectclattachdetach)


This method is only supported by Rustogramer.  It detaches the data source.


### [Query parameters](#query-parameters-2)


None supported.


### [Response format detail](#response-format-detail-2)


A generic response.


#### [Sample Responses.](#sample-responses-2)


Success:


```json
{
    "status" : "OK",
    "detail" : ""
    
}

```




 Mobile navigation buttons 
[[chap7_2_spectrum]]
[[chap7_2_analyze]]



[[chap7_2_spectrum]]
[[chap7_2_analyze]]









 Custom JS scripts
