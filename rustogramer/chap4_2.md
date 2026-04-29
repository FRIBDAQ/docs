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

# [The Parameters Tab](#the-parameters-tab)


The `Parameters` tab allows you to see and modify the metadata associated with paraemters.
Each parameter optionally has the following metadata:


- `Low` The recommended low limit for axes that are defined on this parameter.
- `High` The recommended high limit for axes that are defined on this parameter.
- `Bins` The recommended number of bins between [Low, High).
- `Units` The units of measure of the parameter.


Modifying these metadata will modify the axis definitions that the GUI will suggest for spectra you define with the [[./chap4_1]].


Let's have a look at the `Parameters` tab:


![Parameters tab](./images/parameters_tab.png)


The top part of this GUI contains a parameter chooser and a bunch of buttons.  The bottom part, contains
a tabular list of parameters and their metadata.  You determine which parameters are displayed.


You can edit the contents of the table as follows:


- Clicking the `Append` button adds a new row to the table that will contain the paramete metadata for the parameter currently selected in the parameter chooser.  If the Array checkbox is selected, the parameter is assumed to be  a member of an array of parameters and lines are added for all parameters in the array.
- Clicking the `Replace` button will replace the current selected row in the table with the parameter that is selected in the parameter chooser.  Only one parameter line may be selected for this
  to  operate.
- Clicking `Remove Selected`  will remove all selected rows from the table.


Once the table is populated; you an select any number of rows.  THe selection can be non-contiguous as well.  You can also edit the metadata by typing into the metadata cells in the table.  The `Reload` button will Reload the metadata for all table cells.


The following button operate on the selected rows of the table:


- `Load` - loads the parameter metadata for the selected cells from the server.
- `Set`  - Sets the parameter metadata for the selected cells into the server.
- `Change Spectra` Uses the metadata in the selected parameters to re-define the axis specifications for spectra that use any of the selected parameters.  You will be prompted to confirm along with the names of the affected spectra.




 Mobile navigation buttons 
[[chap4_1]]
[[chap4_3]]



[[chap4_1]]
[[chap4_3]]









 Custom JS scripts
