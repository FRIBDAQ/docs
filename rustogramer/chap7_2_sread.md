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

# [/spectcl/sread requests](#spectclsread-requests)


Requests that a spectrum contenst file be read.  Note that since it is the server itself that does the read, file paths specified must make sense in the context of that server.  This point is important if the client and server don't have a common view of the file system.  For example, systems that don't share filesystem NFS mounts or a native Windows client talking to a server running in a WSL or other type of virtual machine.


## [/spectcl/shared](#spectclshared)


### [Query parameters](#query-parameters)


- **filename** (string) - Required path to file to be read.  This must make sense in the server.
- **format** (string) - Required.  Format in which the file should be written.   Valid format strings are:
  - `ascii` - SpecTcl ASCII format.  This is supported by both SpecTcl and Rustogramer.
  - `binary` - SMAUG binary format.  This is a binary format that should be considered deprecated.
  - `json` - JavaScript Object Notation.  This is supportd by Rustogramer and SpecTcl after version 5.13-012.  For a description of the JSON see [[./chap7_7]].
- **snapshot** (boolean) - Optional defaults to true.  If true spectra read from file are made as snapshot spectra. This means they will not increment:
  - In SpecTcl snapshot spectra are spectra that are wrapped in a special container object that refuses to increment the spectrum.
  - In Rustogramer snapshot spectra are just gated on a special `False` gate.
- **replace** (boolean) - Optional defaults to false.  If true, then if a spectrum is read with the same name as an existing spectrum, the existing spectrum is overwitten.  Otherwise a unique spectrum name is generated.
- **bind** (boolean) - Optional defaults  to true.  If true the spectrum is bound to display shared memory.


### [Response format detail](#response-format-detail)


A generic responses is returned.


#### [Sample Responses.](#sample-responses)


Rustogramer success:


```json
{
    "status" : "OK",
    "detail" : ""
}

```


SpecTcl success:


```json
{
    "status" : "OK"
}

```


Rustogramer fails because the file does not exist:


```json
{
    "status" : "Failed to open input file: /no/such/file",
    "detail" : "No such file or device"
}

```


SpecTcl fails


```json
{
    "status" :  "'sread' command failed",
    "detail" : "<sread command error message>"
}

```




 Mobile navigation buttons 
[[chap7_2_swrite]]
[[chap7_2_trace]]



[[chap7_2_swrite]]
[[chap7_2_trace]]









 Custom JS scripts
