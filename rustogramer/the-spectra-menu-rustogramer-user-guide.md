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

# [The Spectra Menu](#the-spectra-menu)


Many of the items on the `Spectra` menu are available on the `Spectra` tab and `File` menu.
THey are grouped here to make it unecessary to switch tabs to access them:


- [Save spectrum contents.](#save-spectrum-contents)
- [Read spectrum file](#read-spectrum-file)
- [Clear All](#clear-all)
- [Create](#create)
- [Delete](#delete)
- [Apply Gate](#apply-gate)


## [Save Spectrum Contents.](#save-spectrum-contents)


This allows you to save the contents of one or more spectra to file.
See [[./chap4_5#file-save-spectrum-contents]] for a description of the user interface behind this.


## [Read Spectrum File](#read-spectrum-file)


Allows you to read a file that contains the contents of one or more spectra.  See
[[./chap4_5#file-read-spectrum-contents]] for a description of the user interface behind this.


## [Clear all](#clear-all)


Clears the contents of all spectra.  All spectrum channels are set to zero.


## [Create](#create)


Allows you to create one or more spectra.  The spectrum editor tabbed widget is displayed.  When you are done creating the spectra you want, click `Ok` to dismiss the dialog.  A section of the Spectra Tab page describes how to use the [[./chap4_1#the-spectrum-editors]]


## [Delete](#delete)


Allows you to delete one or more spectra.   You can select the spectra to delete using:


![Delete selected](./images/delspectra_dialog.png)


Simply select spectra (you can select more than one at a time). And click the `>` button to add it to the editable list box.  When the listbox contains the spectra you want to delete; click `Ok` to delete those spectra.


Improvements are planned to the spectrum selection  see issue [#170](https://github.com/FRIBDAQ/rustogrammer/issues/170)


You can achieve the same effect in the Spectra tab using the [[./chap4_1#the-button-bar]] on the Spectra tab button bar after selecting the spectra you want deleted from the spectrum listing in that tab.


## [Apply Gate](#apply-gate)


Allows you to apply a gate/condition to one or more spectra;


![Apply dialog](./images/apply-dialog.png)


Select the condition on the left and select however many spectra you want (selections need not be contiguous) on the right and click `Ok` to apply the gate to the selected spectra.




 Mobile navigation buttons 
[[chap4_filters]]
[[chap4_8]]



[[chap4_filters]]
[[chap4_8]]









 Custom JS scripts
