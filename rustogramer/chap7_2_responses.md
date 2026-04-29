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

# [Response format](#response-format)


The response bodies from the server for requests are in Java Script Object Notation or
[JSON](https://www.json.org/json-en.html).


There are several libraries for various programing languages that support decoding JSON.  These are installed at the FRIB:


- C++  - [libjson-cpp](https://open-source-parsers.github.io/jsoncpp-docs/doxygen/index.html) can generate as well as decode JSON.
- Tcl  - [The tcllib json package](https://core.tcl-lang.org/tcllib/doc/tcllib-1-18/embedded/www/tcllib/files/modules/json/json.html)  the companion **json::write** package is used by SpecTcl to generate responses.
- Python - [The requests package](https://requests.readthedocs.io/en/latest/) is a package that can make HTTP requests and decode the resulting response data from Json to Dicts.
- Rust - [The serde framework](https://serde.rs/) provides a framework for seralizing and de-serializing structs to various format using drivers specific to that format.  Rustogramer uses the JSON driver embedded in the Rocket HTTPD framework to generate responses and to decode them in its unit tests for the REST server.   If you want a standalone JSON decoder you might, instead want the
  [Serde JSON package](https://github.com/serde-rs/json) which can be added to your program as shown on that page.


The JSON language docs pointed to above, describes JSON as a set of name/value pairs, where the values can be scalars, arrays or structs (which themselves are name value pairs).   We're going to call the names *keys* for simplicity as most JSON Parsers really don't expose the order of the names to you.


The overarching structure for the REST responses is a struct with two fields whos keys are:


- **status**  - Provides a human readable string that is status of the request as processed by a valid URL handler.  If this value is `OK` the request completed successfully.  If not its value will  be a string containing a human readable error message.
- **detail** - If status was `OK`, this contains data that depends on the actual request.  The value may be a string, a struct or an array.  Read the individual request documentation for information about the shape of the value for this key.


The simplest response type is a struct where the **detail** fields is a string.   Here, for example is a response from the /spectcl/attach/list request:


```json
{
    "status" : "OK",
    "detail" : "Test Data Source"
}

```


As you can see, the requrest succeeded and the ***detail*** key provides the information requested, in this case information about the data source attached to SpecTcl.


This response is used enough times that it has been given a name:  It is referred to in the documentation as a *gheneric response*.  If a page describing a request says that it returns a generic response the struture above is what to expect.


Here is a simple example where the ***detail*** value is a bit more complex; a structure.  This is the response to the /spectcl/version request:


```json
{
    "status" : "OK",
    "detail" : {
        "major"        : 5,
        "minor"        : 14,
        "editlevel"    : "000",
        "program_name" : "SpecTcl"
    }
}

```


Again, the ***status*** field says that the request succeeded and the detail provides several fields identified by the keys **major**, **minor**, **editlevel** and **program_name** which provide the desired information.


Here is an example of a generic response from a `/spectcl/paramter/create?name=event.raw.00` requets that completed in error:


```json
{
    "status" : "'treeparameter -create' failed: ",
    "detail" : "event.raw.00 is already a treeparameter.  Duplicates are not allowed"
}

```


Where a generic response is used, error information usually uses the ***detail*** field to provide additional information about the error.    In this case you can see that the SpecTcl `treeparameter -create` command executed by the REST handler failed and the reason it failed was that there was already a parameter named `event.raw.00` defined.




 Mobile navigation buttons 
[[chap7_2]]
[[chap7_2_parameter]]



[[chap7_2]]
[[chap7_2_parameter]]









 Custom JS scripts
