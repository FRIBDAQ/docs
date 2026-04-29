Provide site root to javascript 

 Work around some values being stored in localStorage wrapped in quotes 

 Set the theme before any content is loaded, prevents flash 


 Hide / unhide sidebar before it is displayed 


1. [[**1.** Chapter 1 - Introduction|chapter_1]]
2. 1. [[**1.1.** How to use this book|chap1_1]]
3. [[**2.** Chapter 2 - Preparing data for Rustogramer|chapter_2]]
4. 1. [[**2.1.** The FRIB analysis pipeline|chap2_1]]
   2. [[**2.2.** Format of data Rustogramer accepts|chap2_2]]
5. [[**3.** Chapter 3 - Running Rustogramer|chapter_3]]
6. [[**4.** Chapter 4 - Using the Rustogramer GUI|chapter_4]]
7. 1. [[**4.1.** The Spectra Tab|chap4_1]]
   2. [[**4.2.** The Parameters Tab|chap4_2]]
   3. [[**4.3.** The Variables Tab|chap4_3]]
   4. [[**4.4.** The Gate Tab|chap4_4]]
   5. [[**4.5.** The BindSets Tab|chap4_bindsets]]
   6. [[**4.6.** The File Menu|chap4_5]]
   7. [[**4.7.** The Data Source Menu|chap4_6]]
   8. [[**4.8.** The Filters Menu|chap4_filters]]
   9. [[**4.9.** The Spectra Menu|chap4_7]]
   10. [[**4.10.** The Gate Menu|chap4_8]]
8. [[**5.** Chapter 5 - Using CutiePie to display histograms|chapter_5]]
9. [[**6.** Chapter 6 - the REST interface|chapter_6]]
10. 1. [[**6.1.** Tcl REST interface|chap6_1]]
   2. [[**6.2.** Python REST interface|chap6_2]]
11. [[**7.** Chapter 7 - Reference material|chapter7]]
12. 1. [[**7.1.** Command Line Options|chap7_1]]
   2. [[**7.2.** REST requests and responses|chap7_2]]
   3. 1. [[**7.2.1.** Response format|chap7_2_responses]]
      2. [[**7.2.2.** /spectcl/parameter requests|chap7_2_parameter]]
      3. [[**7.2.3.** /spectcl/rawparameter requests|chap7_2_rawparameter]]
      4. [[**7.2.4.** /spectcl/gate requests|chap7_2_gates]]
      5. [[**7.2.5.** /spectcl/spectrum requests|chap7_2_spectrum]]
      6. [[**7.2.6.** /spectcl/attach requests|chap7_2_attach]]
      7. [[**7.2.7.** /spectcl/analyze requests|chap7_2_analyze]]
      8. [[**7.2.8.** /spectcl/apply requests|chap7_2_apply]]
      9. [[**7.2.9.** /spectcl/ungate requests|chap7_2_ungate]]
      10. [[**7.2.10.** /spectcl/channel requests|chap7_2_channel]]
      11. [[**7.2.11.** /spectcl/evbunpack requests|chap7_2_evbunpack]]
      12. [[**7.2.12.** /spectcl/filter requests|chap7_2_filter]]
      13. [[**7.2.13.** /spectcl/fit requests|chap7_2_fit]]
      14. [[**7.2.14.** /spectcl/fold requests|chap7_2_fold]]
      15. [[**7.2.15.** /spectcl/integrate requests|chap7_2_integrate]]
      16. [[**7.2.16.** /spectcl/shmem requests|chap7_2_shmem]]
      17. [[**7.2.17.** /spectcl/sbind requests|chap7_2_sbind]]
      18. [[**7.2.18.** /spectcl/unbind requests|chap7_2_ubind]]
      19. [[**7.2.19.** /spectcl/mirror requests|chap7_2_mirror]]
      20. [[**7.2.20.** /spectcl/pman requests|chap7_2_pman]]
      21. [[**7.2.21.** /spectcl/project requests|chap7_2_project]]
      22. [[**7.2.22.** /spectcl/psuedo requests|chap7_2_pseudo]]
      23. [[**7.2.23.** /spectcl/rootree requests|chap7_2_roottree]]
      24. [[**7.2.24.** /spectcl/script requests|chap7_2_script]]
      25. [[**7.2.25.** /spectcl/treevariable requests|chap7_2_treevariable]]
      26. [[**7.2.26.** /spectcl/version requests|chap7_2_version]]
      27. [[**7.2.27.** /spectcl/exit requests|chap7_2_exit]]
      28. [[**7.2.28.** /spectcl/ringformat requests|chap7_2_ringformat]]
      29. [[**7.2.29.** /spectcl/specstats requests|chap7_2_specstats]]
      30. [[**7.2.30.** /spectcl/swrite requests|chap7_2_swrite]]
      31. [[**7.2.31.** /spectcl/sread requests|chap7_2_sread]]
      32. [[**7.2.32.** /spectcl/trace requests|chap7_2_trace]]
   4. [[**7.3.** Shared memory Mirror service|chap7_mirror]]
   5. [[**7.4.** Tcl REST reference|chap7_3]]
   6. [[**7.5.** Python REST reference|chap7_4]]
   7. [[**7.6.** Looking at the Rustogramer internals documentation|chap7_5]]
   8. [[**7.7.** Schema of configuration files|chap7_6]]
   9. [[**7.8.** Format of JSON Spectrum contents files|chap7_7]]
13. [[**8.** Appendix I - Installing Rustogramer|apppendix_1]]






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


[[**|print]]





 Apply ARIA attributes after the sidebar and the sidebar toggle button are added to the DOM 

# [Chapter 4 - Using the Rustogramer GUI](#chapter-4---using-the-rustogramer-gui)


Rustogramer suplies a sample GUI that is based on the NSCLSpecTcl treegui with, what I think are, some improvements in how objects are creatd. The GUI is a sample of a REST client written in Python against the [[Python Rest API|./chap6_2]].


If the envirionment variable `RUST_TOP` is defined to point to the top installation directory of Rustogramer, you can run the gui as follows:


```bash
$RUST_TOP/bin/gui [--host rghost] [[--port rest_port] | [--service rest_service] [--service-user rg_user]]

```


The gui supports the following command options


- `--host` specifies the host on which the rustogramer you want to control is running.  This defaults to `localhost` if not specified.
- One of two methods to specify the REST port that Rustogramer is using:
  - `--port` specifies the numeric port on which Rustogramer's REST server is listening.  This defaults to `8000` which is Rustogrammer's default REST port.
  - If rustogramer is using the NSCLDAQ port manager to advertise a service name:
    - `--service`  specifies the name of service rustogramer is advertising.
    - `--service-user` specifies the name of the user that rustogramer is running under.  This defaults to your login username and, in general, should not be used.


When connected to Rustogramer, the GUI will look like this:
![Initial GUI view](images/gui_spectra.png)


Prior to describing each of the user interface elements let's look at a few features of this image.


- The menubar at the top of the window provides access to operations that are not as frequent as those available on the main window.  Note that the contents of the menubar depends on the actual application the GUI is connectec to.
- The tabs below the menu-bar provide access to the sections of functionality of the GUI.  Note that the set of tabs will, again, depend on the application the GUI is connected to.   For example, Rustogramer does not have TreeVariable like functionality as that capability is pushed back onto the code that prepares data-sets.  If connected to SpecTcl, however, a `Variables` tab will be present.
- Below the Tabs are controls for the things that Tab manages.  In the figure above, the `Spectra` tab is selected and shows a tabbed notebook that allows you to create and edit the definitions of Spectra as well as a filtered list of spectra and their applications.  More about this tab in the documentation [[the spectra tab|./chap4_1]]
- Note that the only thing the `Help` menu provides is information about the program (the `About` menu command).


For information about the contents of each tab:


- [[The `Spectra` Tab|./chap4_1]]
- [[The `Parameters` Tab|./chap4_2]]
- [[The `Variables` Tab|./chap4_3]] (SpecTcl only).
- [[The `Gate` Tab|./chap4_4]]
- [[The `BindSets` Tab|./chap4_bindsets]]


For information about the Menus:


- [[The `File` Menu|./chap4_5]]
- [[The `Data Source` Menu|./chap4_6]]
- [[The `Filters` Menu|./chap4_filters]] (SpecTcl only).
- [[The `Spectra` Menu|./chap4_7]]
- [[The `Gate` Menu|./chap4_8]]


The rustogramer GUI is now included in SpecTcl (as of version 7.0).  To use it you'll need to setup the ReST server as described in the CutiePie documentation.  You can then start the GUI from `SpecTclRC.tcl`
by adding the line:


```tcl
exec python3 $SpecTclHome/pythontree/Gui.py --port $HTTPDPort &

```


towards the end of that file.




 Mobile navigation buttons 
[[**|chapter_3]]
[[**|chap4_1]]



[[**|chapter_3]]
[[**|chap4_1]]









 Custom JS scripts
