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

# [Chapter 1 Introduction](#chapter-1-introduction)


## [What is Rustogramer](#what-is-rustogramer)


Rustogramer is a histograming application written in the Rust programming language.


The Rust programing language is a language that is optimized for reliable programing.
By this I mean:


- It is very hard to generate memory leaks in Rust programs.
- Threading is layered on the language in a way that  makes many of the issues normally associated with threading (race conditions, deadlocks) very difficult.


The support for reliable programing in Rust makes it a good choice for mission critical software at the FRIB.


Rustogramer is written as a closed program.  Unlike NSCLSpecTcl, for example,  you don't have to and are not allowed to write user code sections to make a version of Rustogramer suitable for use.
This is good because:


- Most SpecTcl ``bugs'' are actually errors in user code.
- You won't have to learn Rust to use Rustogramer.


Other interesting features of Rustogramer:


- It is portable between Linux and Windows.  It may well run on OS-X but we don't test/debug on that system so no assurances.  With the FRIB standard desktop a Windows system, this means you can extend you data analysis to the power of your desktop system.
- It is noninteractive.  This allows you to run it in the background, only interacting with it as desired.
- It is compatible with the CutiePie visualizer see [FRIB docs on CutiePie](https://docs.nscl.msu.edu/daq/newsite/qtpy/index.html)
- It provides a REST-like interface that allows you to interact with it either through the provided Python GUI or with any GUI you might write in Python or Tcl.  Since REST protocols are inherently stateless, you can start or stop any number of GUIs at any time.




 Mobile navigation buttons 
[[chap1_1]]



[[chap1_1]]









 Custom JS scripts
