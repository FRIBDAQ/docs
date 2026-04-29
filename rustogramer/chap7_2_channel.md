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

# [/spectcl/channel requests](#spectclchannel-requests)


The requests in this domain support accessing single channels of a spectrum:


- [/spectcl/channel/set](#spectclchannelset) allows you to set the value of a channel.
- [/spectcl/channel/get](#spectclchannelget) provides the value of a channel


## [/spectcl/channel/set](#spectclchannelset)


Sets the value of a single bin/channel in  a spectrum.


### [Query parameters](#query-parameters)


- **spectrum** (string) - mandatory parameter that provides the name of the spectrum ot modify.
- **xchannel** (unsigned) - mandatory parameter that provides the bin on the X axis to set.
- **ychannel** (unsigned) - optional parameter that provides the bin on the Y axis to set for spectra with X and Y axes.  For spectra without a Y bin axis, this can be omitted.
- **value** (float) - mandatory paramter that provides the new value for the channel.


### [Response format detail](#response-format-detail)


The response is a generic respones.


#### [Sample Responses.](#sample-responses)


Successful return:


```json
{
    "status":"OK",
    "detail":""
}

```


Failure (no such spectrum):


```json
{
    "status":"Unable to set channel: ",
    "detail":"No such spectrum: araw.04"
}

```


Failure (bad channel number):


```json
{
    "status":"Unable to set channel: ",
    "detail":"X index is out of range"
}

```


## [/spectcl/channel/get](#spectclchannelget)


Returns the value of a channel of a spectrum.


### [Query parameters](#query-parameters-1)


- **spectrum** (string) - mandatory parameter that provides the name of the spectrum ot modify.
- **xchannel** (unsigned) - mandatory parameter that provides the bin on the X axis to set.
- **ychannel** (unsigned) - optional parameter that provides the bin on the Y axis to set for spectra with X and Y axes.  For spectra without a Y bin axis, this can be omitted.


### [Response format detail](#response-format-detail-1)


The detail of this request, on success, is a floating point value (generally the float is a valid unsigned integer).


#### [Sample Responses.](#sample-responses-1)


Succes:


```json
{
    "status":"OK",
    "detail":1234.0
}

```


Failure (bad channel):


```json
{
    "status":"Could not get channel: X index is out of range",
    "detail":0.0
}

```


While this shows the **detail** field to be zero, you should not rely on that.  If **status** is not `OK` you must ignore the **detail** field.


Failure (no such spectrum):


```json
{
    "status":"Could not get channel: No such spectrum 'araw.04'",
    "detail":0.0
}
```




 Mobile navigation buttons 
[[chap7_2_ungate]]
[[chap7_2_evbunpack]]



[[chap7_2_ungate]]
[[chap7_2_evbunpack]]









 Custom JS scripts
