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

# [The Filters Menu (SpecTcl Only).](#the-filters-menu-spectcl-only)


As we have described in [[./chap4_6#data-source-filter-file-spectcl-only]] menu  SpecTcl an write filtered event data files.  See that section for more information about what filter files are and pointers to SpecTcl documentation on filter files.   The `Filters` menu provides:


- The ability to create filters via a [filter wizard](#filter-filter-wizard).
- The ability to [control which filters are enabled](#filter-enabledisable-filters); enabled filters write data.
- Another menu entry to [attach a filter file](#filter-read-filter-files) for analyais.


Note again, that these menu entries are only available with SpecTcl and on rustogramer, the Filter menu itself will ont be present.


## [Filter->Filter Wizard](#filter-filter-wizard)


Creating a filter is a multi-step process.  The filter wizard leads you through the process of:


- [Naming the filter](#naming-the-filter)
- [Selecting, if desired, a gate](#selecting-the-filter-gate) to determine which events are written to the  filter file.
- [Choosing the parameters](#selecting-the-parameters-to-output) to write for each event that makes the gate true.
- [Choosing the file](#choosing-the-output-file) to which filter data will be written and whether the filter should be created
  enabled.


The next subsections will look at each of these steps, showing you the Wizard GUI for each step:


### [Naming the filter.](#naming-the-filter)


THe firs step of the filter wizard:


![Filter name](./images/fwiizard_name.png)


Describes the process of making a filter and presents you with an editable text input in which you can type the filter's name.  Filter names must be unique.


When you are satisfied with your filter name, click the `Next >` button.


### [Selecting the filter gate](#selecting-the-filter-gate)


A filter is gated.   Only events that make the filter true are written to the output file.  This allows you to do things like write only events with a specific particle ID for example.  The second stage of the filter wizard prompts you for a filter gate:


![Filter gate](./images/fwizard_gate.png)


Select a gate from the pull down:


- If you've updated the gates your gate may not be visible. Clicking the `Update Gate list` button, will then update the list of gates that populate the gate chooser pull-down.
- If you want all events to be written, create and select a `True` gate as the filter gate.


When you hvae the desired gate selected, click the `Next >` Button.


### [Selecting the parameters to output.](#selecting-the-parameters-to-output)


Only a subset of parameters need to be written to filter files.  The next stop provides a parameter chooser/editable list to allow you to choose the parameters you want output:


![Filter parameters](./images/fwizard_params.png)


Improvements to this stage of the GUI are planned see Issue [#169](https://github.com/FRIBDAQ/rustogrammer/issues/169) for more information.   When the parameters you want written are all in the editable list box, click the `Next >` button to advance to the last stage of the wizard.


### [Choosing the output file.](#choosing-the-output-file)


The final step of the filter creation process is to specify where the filtered data will be written and, optionally to enable the filter.


![File](./images/fwiizard_file.png)


Only enabled filters will actually write data.


## [Filter->Enable/Disable Filters](#filter-enabledisable-filters)


This menu entry allows you to enable and disable filters.  It brings up this dialog:


![Enable filters](./images/filter_enables.png)


The table has a line per filter.  The left column are filter names and the right columns checkboxes.  Check the boxes for the filters you want enbled then click the `Ok` button to apply your selections.


## [Filter->Read Filter Files](#filter-read-filter-files)


This menu command allows you to attach a filter file.  THe mechanics of this are described in
the [[chap4_6#data-source-filter-file-spectcl-only]].




 Mobile navigation buttons 
[[chap4_6]]
[[chap4_7]]



[[chap4_6]]
[[chap4_7]]









 Custom JS scripts
