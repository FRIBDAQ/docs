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

# [The BindSets Tab](#the-bindsets-tab)


This section describes the Bindsets tab.  Before describing how to use that tab let's take a bit of time to
describe what a bindset it and why they can be useful.


Both SpecTcl and Rustogramer don't have intrinsic visualizers for their spectra.  These are supplied by external, programs such as CutiePie.  SpecTcl and Rustogramer both provide a display shared memory region in which spectra that can be visualized are stored.   The process of storing spectra in this shared memory is called `sbinding` and the process of removing a spectrum from the shared memory is called `unbinding`.  Sbinding and unbinding have no effect on spectrum contents.


Both Spec Tcl and Rustogrammer can support as many spectra and as much spectrum data as virtual memory allows.  *However*  the shared memory size is fixed at program start.  In the past, SpecTcl GUIs attempted to just sbind all spectra.  As analysis becomes more complex and the amount of spectrum storage increases, this is less and less feasible.  Thus bindsets.


## [What are bindsets](#what-are-bindsets)


A bindset is:


- A name
- A description
- A list of spectra.


The GUI supports loading bindsets into shared memory (either first unbinding the spectra in shared memory first or supplementing the set of spectra already sbound int shared memory).   Think of a bindset as a group of spectra that you will tend to want to look at for some period of time.  The idea is that the set of spectra you need to see when you are setting up an experiment, debugging detectors and electrons, may well be different from the set of spectra you want to see at various points of running the experiment with beam.  Bindsets support loading only the spectra you want to see at any given time into the display shared memory.


The Bindests tab supports:


- Saving the currently bound spectrum in a new or existing bindset.
- Creating a new bind set.
- Editing an existing bind set.
- Loading a bind set into shared memory.
- Adding the spectra in a bind set to those in shared memory.
- Attempting to sbind all spectra into shared memory.


Furthermore, the `File->Save...` menu operation saves the bindsets you've defined to the database file and `File->Load...` loads them from the selected database file.


## [The BindSets tab contents](#the-bindsets-tab-contents)


The BindSets tab looks like this:


![BindSets tab contents](./images/bindsettabs.png)


At the center of the user interface is a table (which becomes scrollable if needed).  The table lists the bind sets you have defined along with their descriptions.  At any time you
can select one of the bind sets by clicking on it.


If you have loaded a bindset, its name and description are loaded into the labels above the table.  The buttons that have the text `Selected` in their labels require that you have selected a bindset in the table and operate on the selected bindset.


The buttons are in logical rather than visual order:


- [New...](#new-bindset) - makes a new bindset.
- [Edit Selecteed...](#edit-bindset) - edits the selected bindeset.
- Load Selected - Loads the selected bindset in to shared memory after first unbinding any spectra that are there.
- Add Selected - Attempts to add the selected bindest to those in shared memory.
- [Save as selected...](#save-selected) - Save the currently bound spectra to the selected bindset
- [Save as new...](#save-new) - Save the currently bound spectra to a new bindset.
- Bind All - attempts to  bind all defined spectra to the display memory.
- Update (spectra) - updates the spectra known to the bindset editors from the histogramer


### [New bindset](#new-bindset)


Clicking the `New...` button pops up a dialog that contains the bind set editor:


![Bind set editor](./images/bindset-editor.png)


At the top are entries for the bindset name and description. The description can be omitted, though this is not recommended.  The bindset name is mandatory.


The list at the left of the editor is the list of spectra that can be put into the bind set. It's called the source list.  The list at the right is the set of spectra you've currently got in the bind set.  Add spectra to the bindset by selecting any number of spectra from the source list and clicking the right arrow button between the two lists.  When you do this the spectra are removed from the source list and appended to the right listbox.


You can also select spectra from the right box and click X to remove them (they will be added
back to the source list).  The Clear button removes all spectra from the right list adding
them back to the source list.  The up/down arrows move the selected spectra up or down in the
right list box and are just there to allow you to organize that box.


When you are happy with the bindset you've created, click the Ok button.  To abort the creation of the bind list, click the Cancel button.


### [Edit bindset](#edit-bindset)


The `Edit Selected...` button also pops up the bind set editor described in
the [New bind set](#new-bindset) section.  However, the editor is first populated with the
name and description of the selectged bind set. The right list box is populated with the spectra in the bind set and those spectra do not appear in the source list.


### [Save selected](#save-selected)


Pops up the bind set editor with the name and description of the editor populated from the selected bindset but the right listbox, populated from the spectra that are currently bound in the shared memory.


### [Save new](#save-new)


Pops up the bind set editor with the name and description not populated but the right listbox populated from the spectra currently bound to shared memory.




 Mobile navigation buttons 
[[chap4_4]]
[[chap4_5]]



[[chap4_4]]
[[chap4_5]]









 Custom JS scripts
