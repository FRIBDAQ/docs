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

# [Preparing data for Rustogramer](#preparing-data-for-rustogramer)


## [How Rustogramer differs from SpecTcl](#how-rustogramer-differs-from-spectcl)


The material in this chapter describes how to prepare a data set for Rustogramer.  This differs a bit from what you are used to if you came to Rustogramer from NSCLSpecTcl.


In [NSCLSpecTcl](https://docs.nscl.msu.edu/daq/newsite/spectcl-5.0/pgmguide/index.html), analyzing a data set required that you prepare a data analysis pipeline that you then used to create a customized version of NSCLSpecTcl.


The event processing pipeline then ran each time you processed an event file to turn the raw event data into  a set of parameters that could then be histogramed.  If you had an error in your event processing pipeline, your modified SpecTcl could crash.   Furthermore, if you had to analyze an event file more than once, you would do this decode each time you analyzed that event file.


Rustogramer expects the processing that was done by the NSCLSpecTcl event processing pipeline to be done by an external program *that only runs once on each event file*.
While you can do this processing any way you want; we recommend you use the FRIB analysis pipeline as described [[./chap2_1]] to create the processed event data files expected by Rustogramer (as a side note, beginning with  version 5.13, NSCLSpecTcl can also take these files as input and bypass the event processing pipeline to go straight to histograming).


The FRIB analysis pipeline supports:


- Paralelizing the decoding of events.
- Taking input from a previous pass and extending the data (e.g. with computed parameters) to produce another data-set.
- By combining these two mechanisms, you can compute that which can be parallelized in one process, which is run parallelized, and those which cannot (e.g. cross event computations) in another which is not parallelized.




 Mobile navigation buttons 
[[chap1_1]]
[[chap2_1]]



[[chap1_1]]
[[chap2_1]]









 Custom JS scripts
