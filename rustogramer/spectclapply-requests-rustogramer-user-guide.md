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

# [/spectcl/apply requests](#spectclapply-requests)


Conditions are only useful when applied to a spectrum.  When a condition/gate is applied to a spectrum it is said to *gate that spectrum*.  This means that for events, which normally could increment the histogram, that increment will only occur if the gate is satisfied  (the condition is true for that event).


The `/spectcl/apply` domain of URIs allow you to apply unapply and list applications:


- [`/spectcl/apply/apply`](#spectclapplyapply) - Applies a gate/condition to one or more spectra.
- [`/spectcl/apply/list`](#spectclapplylist) - Produces a list of gates applied to spectra.
- [`/spectcl/ungate`](#spectclungate) - Removes any gate a spectrum has.


## [/spectcl/apply/apply](#spectclapplyapply)


Applies a gate to one or more spectra.


### [Query parameters](#query-parameters)


- **gate** - Name of the gate to apply.
- **spectrum** A spectrum to apply the gate to.  In rustogramer, this can appear more than once; e.g. `../spectcl/apply?gate=agate&spectrum=larry&spectrum=moe&spectrum=curly`
  applies the gate `agate` to the spectra `larry`, `curly` and `moe`


### [Response format detail](#response-format-detail)


Generic rsponse


## [/spectcl/apply/list](#spectclapplylist)


List the gates applied to spectra.


### [Query parameters](#query-parameters-1)


- **pattern** - glob pattern that, filters the listing to only contain spectra that match the pattern.  If not supplied defaults to `*` and all spectra are listed.


### [Response format detail](#response-format-detail-1)


The detail is a vector of structs with the fields:


- **spectrum** - name of a spectrum.
- **gate** - Name of the gate applied to the spectrum.


In SpecTcl, spectra are always gated.  When reated they are gated by the `-TRUE-` gate which is always true.  In Rustogramer, spectra can be ungated in which case the **gate** field is `null`


#### [Sample Responses.](#sample-responses)


```json
{
    "status" : "OK",
    "detail" : [{
        "spectrum" : "raw.00",
        "gate"     : "-TRUE-"
    }]
}

```


This represents an ungated spectrum.


## [/spectcl/ungate](#spectclungate)


Removes the gate from one or more spectra.


Note that in Rustogramer spectra can exist without gates.  In SpecTcl, all spectra are gated and this operation gates the specrat with the `-Ungated-` gate which  is a True gate.


### [Query parameters](#query-parameters-2)


- **name** name of a spectrum to ungate.   This parameter an appear more than once and allows you to ungate more than one spectrum.


### [Response format detail](#response-format-detail-2)


Generic response


#### [Sample Responses.](#sample-responses-1)


Here's an error return from SpecTcl attempting to ungate a spectrum `event.raw.00` that dos not exist:


```json
{
  "status": "'ungate' command failed",
  "detail": "{event.raw.00 {Failed search of dictionary by Key string\nKey was:  event.raw.00 Id was: -undefined-\n}}"
}

```




 Mobile navigation buttons 
[[chap7_2_analyze]]
[[chap7_2_ungate]]



[[chap7_2_analyze]]
[[chap7_2_ungate]]









 Custom JS scripts
