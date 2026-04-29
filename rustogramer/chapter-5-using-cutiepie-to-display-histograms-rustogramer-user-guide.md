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

# [Chapter 5 - Using CutiePie to display histograms](#chapter-5---using-cutiepie-to-display-histograms)


The [Cutie Pie Displayer](http://github.com/FRIBDAQ/CutiePie) uses the  spectrum shared memory mirroring capability of SpecTcl and Rustogramer as well as the REST interface to allow you to display and interact with the histograms produced by both programs.  CutiePie can run in both Linux and Windows, bringing, along with rustogramer,  fully functional histograming to the Windows desktop.


At the FRIB, the standalon CutiePie will normally be installed in `/usr/opt/cutiepie/`*x.y-nnn* where x.y.nnn is the version of CutiePie.  To run Cutiepie assuming you have defined the environment variable CUTIETOP to point at this directory:


```
$CUTIETOP/bin/CutiePie

```


In Windows, typically CutiePie is installed in `C:\CutiePie` and you can start it via


```
\CutiePie\bin\cutiepie

```


Naturally, in windows, you can make a desktop shortcut.


When Cutiepie is running,  Use it's `Connect` button to connect it to SpecTcl or Rustogramer.
Note that due to differences in how shared memory and mirroring works between Linux and Windows, you cannot mix environments.  You can only:


1. Run native Windows CutiePie with native Windows Rustogramer.
2. Run Linux/WSL CutiePie with Linux/WSL Rustogramer or SpecTcl.


For CutiePie user documentation see [The FRIB documentation page on CutiePie](https://docs.nscl.msu.edu/daq/newsite/qtpy/index.html)




 Mobile navigation buttons 
[[chap4_8]]
[[chapter_6]]



[[chap4_8]]
[[chapter_6]]









 Custom JS scripts
