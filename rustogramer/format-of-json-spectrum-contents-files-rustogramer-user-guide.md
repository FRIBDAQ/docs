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
[[chap7_6]]
[[apppendix_1]]



[[chap7_6]]
[[apppendix_1]]









 Custom JS scripts
