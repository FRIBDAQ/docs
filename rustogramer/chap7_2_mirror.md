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

# [Shared memory Mirror service](#shared-memory-mirror-service)


SpecTcl maintains a list of all of the mirror clients that have registered with it.  See the [[./chap7_mirror]] for more information about the mirror server protocol in general and mirror registration specifically.


The registration of a mirror client provides the host on which the client runs and the shared memory it created.  SpecTcl's mirror client application and API use this to share mirrored shared memories between clients.   The mirror client either establishes a new mirror, if one does not yet exist for the host, or maps to the existing mirror if there already is one.


Rustogramer provides this service as well.  Note that in windows, it's assumed there's typically only one client so the client code unconditionally creates a new mirror internal to the process that requests it.


## [/spectcl/mirror](#spectclmirror)


Returns a list of the mirrors being remotely maintained.


### [Query parameters](#query-parameters)


No query paramters are supported.


### [Response format detail](#response-format-detail)


The **detail** is an array of structs where each struct describes a mirror registration and contains the following attributes:


- **host** (string) - DNS name or IP address in dotted notation of the host maintaining a mirror.
- **shmkey** (string) - Shared memory identifier.  See the [[./chap7_2_shmem]]


#### [Sample Responses.](#sample-responses)


```json
{
    "status" : "OK",
    "detail" : [
        {
            "host" : "some.host.at.adomain",
            "shmkey" : "Xa3b"
        }
    ]
}

```




 Mobile navigation buttons 
[[chap7_2_ubind]]
[[chap7_2_pman]]



[[chap7_2_ubind]]
[[chap7_2_pman]]









 Custom JS scripts
