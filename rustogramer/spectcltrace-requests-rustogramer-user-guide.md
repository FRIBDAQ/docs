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

# [/spectcl/trace requests](#spectcltrace-requests)


Under ordinary circumstances, a ReST client that wants to be informed of changes to parameter, spectra and condition/application definitions would need to periodically issue requests to list these and analyze the differences between results from a prior time.  This can be computationally and bandwidth expensive, especially for large analysis configurations.


Traces are a scheme that reduces this load.  Traces are a mechanism that allow applications to be informed of changes to the analysis configuration.  The application:


- Establishes a trace using [`/spectcl/trace/establish`](#spectcltraceestablish).  This declares the desire for a client to use the trace system.  The server returns a token the client should use in subsequent trace requests.
- Periodically, the client asks for changes since the last time it asked for changes using [`/spectcl/trace/fetch`](#spectcltracefetch) supplying its token.
- When the client exits, it ideally issues [`/spectcl/trace/done`](#spectcltracedone) providing its token.  All resources associted with this token are released and the token is rendered invalid.


As the server runs, changes in parameter, spectrum, condition and condition application are queued for each token.  You might be concerned that these queues can grow without bound if clients either stop polling without doing a done, or just exit in error due to program errors.  That is a valid concern.


When tracing is established, the client must, therefore pass a retention time which s associated with the client's queue (identified by the client token returned).  As traces are added, all trace records older than this retention time are removed from the queue.  This serves to bound the storage requirements in the server for a queue for a dead client.


Both SpecTcl and Rustogramer support traces.  As described above:


- [`/spectcl/trace/establish`](#spectcltraceestablish) is requested first to associated a token with the clietn, and create a trace queue for the client with a retention time.
- [`/spectcl/trace/fetch`](#spectcltracefetch) - fetches the trace records that have been queued for the client since the last time this request was issued that are not older than the retention time.
- [`/spectcl/trace/done`](#spectcltracedone)  is issued by the client to indicate that it is done using the trace subsystem (usually clients issue this as part of their exit code).


## [/spectcl/trace/establish](#spectcltraceestablish)


Establish trace queues for a client.


### [Query parameters](#query-parameters)


- **retention** (unsigned integer > 0)- Mandatory.  Number of seconds in the retention interval.  Note that this is a minimum retention time as it is the queuing of new trace data that performs the pruning of old trace data.


### [Response format detail](#response-format-detail)


*detail* is an integer value; the trace token generated to identify the client.


#### [Sample Responses.](#sample-responses)


Successful completion


```json
{
    "status" : "OK",
    "detail" : 17394
}

```


In the example above, the client should use the token value `17394` to identify itself.


## [/spectcl/trace/fetch](#spectcltracefetch)


Fetch the traces associated with the client.  This is destructive in the sense that once a trace has been fetched it will no longer be in the trace queue.   Thus fetches fetch the traces since the last fetch operation  (which have not aged out).


### [Query parameters](#query-parameters-1)


- **token** - Value of the token gotten from [`/spectcl/trace/establish`](#spectcltraceestablish).


### [Response format detail](#response-format-detail-1)


**detail** is a struct containing the following attributes.


- **parameter** - The traces on parameters.
- **spectrum** - The traces on spectra.
- **gate** - Traces on gates (conditions).
- **binding** - Traces on bindings of spectra to shared memory.


The value of each trace is a string array.  Each element of the string array describes a trace.  The first word of a trace is the operation that was done to fire the trace and the second the name of the object on which the trace fired.


Trace operations are:


- add - the named item was aded.
- changed - the named item was deleted.
- delete - the named item was deleted.


Bindings traces have the name and the binding id and their operations are:


- add - the named spectrum was bound to display shared memory and assigned the binding id.
- remove - the named spectrum with the bindgin id was removed from shared memory.


#### [Sample Responses.](#sample-responses-1)


Here is an example showing the pre-existing spectrum `george` was just modified.  Note that spectrum modification means deleting the old one and adding a new one.


```json
{
    "status" : "OK",
    "detail" : {
        "parameters" : [],
        "spectrum" : [
            "delete george",
            "create george"
        ],
        "gate" : [],
        "binding" : []
    }
}

```


## [/spectcl/trace/done](#spectcltracedone)


Stop accumulating trces for a specific client.


### [Query parameters](#query-parameters-2)


- **token** (unsigned) - Mandatory - the token returned when requesting [`/spectcl/trace/establish`](#spectcltraceestablish).


### [Response format detail](#response-format-detail-2)


**detail** is a generic response.


#### [Sample Responses.](#sample-responses-2)


Success in Rustogramer:


```json
{
    "status": "OK",
    "detail" : ""
}

```




 Mobile navigation buttons 
[[chap7_2_sread]]
[[chap7_mirror]]



[[chap7_2_sread]]
[[chap7_mirror]]









 Custom JS scripts
