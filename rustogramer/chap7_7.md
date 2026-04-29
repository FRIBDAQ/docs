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

# [Format of JSON Spectrum contents files](#format-of-json-spectrum-contents-files)


Rustogramer and SpecTcl, as of 5.13-013 and later, can write spectrum files in JavaScript Object Notation (JSON).
JSON is a descriptive text format.   For a description of JSON syntax and semantics, see the home page of [the JSON organization](https://www.json.org/json-en.html).  The remainder of this section assumes that you have some basic understanding of JSON syntax and semantics.


Rustogramer uses the serde crate with the Rocket JSON driver to read/write its files while SpecTcl uses the  json-cpp library.


At the top level, the file is just an array of objects.  Each object has the following attributes:


- **definition** - Is an object that describes the spectrum.
- **channels** - Is an array of objects;  Each object a bin in the spectrum with non-zero counts.


Note that it is legal for **channels** to describe bins with no counts, but this is not done in order to compress 2-d spectra which often are naturally sparse.


## [The definition Object](#the-definition-object)


The purpose of the definition object is to capture all of the information required to reconstruct the spectrum definition.  It consists of the following attributes:


- **name** (string) - the original spectrum array.
- **type_string** (string) the SpecTcl spectrum type string.  See the **spectrum** command in the [SpecTcl Command Reference](https://docs.nscl.msu.edu/daq/newsite/spectcl-5.0/cmdref/index.html) for the possible values of this string.
- **x_parameters** (array) - An array of strings.  Each string is the name of a parameter on the X axis of the spectrum.
- **y_parameters** (array) - An array of strings.  Each string is the name of a parameter on the Y axis of the spectrum.
- **x_axis** (array) - an array of three elements that contain the low (float), high (float) and bins (unsigned) for the X axis.
- **y_axis** (array) - An array of three elements that define the Y axis (same order as **x_axis**).  If the spectrum has no Y axis, Rustogramer will insert a `null` here while SpecTcl will provide an empty array.


Here is a sample 1-D definition object written by Rustogramer:


```json
...
"definition":
    {"name":"1","type_string":"1",
    "x_parameters":["parameters.05"],
    "y_parameters":[],
    "x_axis":[0.0,1024.0,1026],
    "y_axis":null},
    ...

```


Here is a sample 2-D definition object:


```json
...
"definition":
    {"name":"2","type_string":"2",
    "x_parameters":["parameters.05"],
    "y_parameters":["parameters.06"],
    "x_axis":[0.0,1024.0,1026],
    "y_axis":[0.0,1024.0,1026]},
...

```


The 1-d spectrum definition written by SpecTcl would look like:


```json
...
"definition":
    {"name":"1","type_string":"1",
    "x_parameters":["parameters.05"],
    "y_parameters":[],
    "x_axis":[0.0,1024.0,1026],
    "y_axis":[]},
    ...

```


Note that the **y_axis** attribute is an empty array rather than **null**


## [Spectrum Contents.](#spectrum-contents)


The spectrum contents are the **channels** attribute of the spectrum and that's an array of objects with the following attributes:


- **chan_type**  (string) the type of the channel.  For the most part this should be `Bin` indicating that this is an ordinary bin.  Rustogramer may also provide `Underflow` and `Overflow` indicating the channel in question represents under or overflow counts.
- **x_coord** (float) - the real X coordinate of the bin.
- **y_coord** (float) - the real Y coordinate of the bin.  Only expect this to have a reaonsalbe value if the spectrum has two axes.
- **x_bin** (unsigned) - X bin number.
- **y_bin** (unsigned) - Y Bin number; again, only expect this to have a reasonable value if the spectrum has two axes.
- **value** (unsigned) - Number of counts in this bin.  As rustogramer and SpecTcl are written at this time, this should aways be non zero. You should assume that omitted channels have no counts.


Here is a sample **channel** object from a 1-d spectrum:


```json
...
 {"chan_type":"Bin",
    "x_coord":500.0,"y_coord":0.0,
    "x_bin":501,"y_bin":0,"value":163500}
...

```


Here is a sample **channel** object fomr a 2-d spectrum:


```json
...
{"chan_type":"Bin",
    "x_coord":500.0,"y_coord":600.0,
    "x_bin":501,"y_bin":602,"value":163500}
...

```


## [Sample JSON spectrum file.](#sample-json-spectrum-file)


Below is a sample spectrum file that contains a 1d spectrum named `1` and a 2d spectrum named `2`. Each spectrum only has a pseudo pulse peak:


```json
[
    {"definition":
       {"name":"1","type_string":"1",
       "x_parameters":["parameters.05"],
       "y_parameters":[],
       "x_axis":[0.0,1024.0,1026],
       "y_axis":null},
       "channels":[
        {"chan_type":"Bin",
         "x_coord":500.0,"y_coord":0.0,
         "x_bin":501,"y_bin":0,"value":163500}]},
    {"definition":
    {"name":"2","type_string":"2",
    "x_parameters":["parameters.05"],
    "y_parameters":["parameters.06"],
    "x_axis":[0.0,1024.0,1026],
    "y_axis":[0.0,1024.0,1026]},
    "channels":[
        {"chan_type":"Bin",
        "x_coord":500.0,"y_coord":600.0,
        "x_bin":501,"y_bin":602,"value":163500}]}
]

```


This was written by Rustogramer.  Had this been written by SpecTcl, the only difference would be the **y_axis** attribute of the first spectrum, which would be an empty array rather than `null`




 Mobile navigation buttons 
[[**|chap7_6]]
[[**|apppendix_1]]



[[**|chap7_6]]
[[**|apppendix_1]]









 Custom JS scripts
