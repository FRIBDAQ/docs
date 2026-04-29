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

# [/spectcl/pman requests](#spectclpman-requests)


This domain of URIs only is supported by SpecTcl.  SpecTcl transforms raw event data into parameterized data via a logical *analysis pipeline*.  The pipeline consists of stages called *event processors*.  Each event processor has access to the raw event as well as the unpacked parameters at that stage of the pipeline.  As such, event processors can, not only decode raw data into parameters, but create computed parameters independent of the format of the raw data.


Rustogramer is built to operate on decoded parameter sets rather than raw data so that the process of creating parameters does not have to happen over and over again for each analysis pass.  Therefore analysis pipeline manipulation makes no sense.


In SpecTcl 5.0 and later, commands and APIs were introduced to allow event processors to be incorporated and registered but not, necesarily, made part of the event processing pipeline in use.  The `pman` command, describedi n the [`SpecTcl Command Reference`](https://docs.nscl.msu.edu/daq/newsite/spectcl-5.0/cmdref/index.html) is the user side of this SpecTcl subsystem.


The requests in this URI domain provide support for dynamically composing event processing pipelines and selecting the pipeline to be used with the analyzed data.  One very simple use case for this would be to register the filter unpacker and make a pipeline for it while also making a raw event decoding pipeline.  One could then switch between processing raw and filtered data without modifying or switching SpecTcl by selecting the appropriate pipeline for the data set.


The following URIs are supported:


- [`/spectcl/pman/create`](#spectclpmancreate) - Create a new, empty, event processing pipeline.
- [`/spectcl/pman/ls`](#spectclpmanls) - List just the names of the event procesing pipelines currently defined.
- [`/spectcl/pman/current`](#spectclpmancurrent) - Return the  currently selected pipeline.
- [`/spectcl/pman/lsall`](#spectclpmanlsall) - List processing pipelines and the event processors in them.
- [`/spectcl/pman/lsevp`](#spectclpmanlsevp) - Lists the names of the event processors.
- [`/spectcl/pman/use`](#spectclpmanuse) - Select the current event processing pipeline.
- [`/spectcl/pman/add`](#spectclpmanadd) - Add an event processor to the end of an event processing pipeline.
- [`/spectcl/pman/rm`](#spectclpmanrm) - Remove an event processor from a pipeline.
- [`/spectcl/pman/clear`](#spectclpmanclear) - Remove all event processors from a pipe.
- [`/spectcl/pman/clone`](#spectclpmanclone) - Create a duplicat of an existing pipeline.


## [/spectcl/pman/create](#spectclpmancreate)


SpecTcl only - create a new event processing pipeline.  The pipeline will have no event processors.


### [Query parameters](#query-parameters)


- **name** (string) - Name of the processor to create.


### [Response format detail](#response-format-detail)


Generic response


#### [Sample Responses.](#sample-responses)


From rustogramer:


```json
{
    "status": "Pipeline management is not implemented",
    "detail": "This is not SpecTcl",
}

```


From SpecTcl success:


```json
{
    "status": "OK"
}

```


From SpecTcl failure: j


```json
{
    "status" :  "'pman mk' command failed",
    "detail" : "<Error message from pman mk command>"

}

```


## [/spectcl/pman/ls](#spectclpmanls)


Lists just the names of the pipelines. To get more information, see  [/spectcl/pman/lsall](#spectclpmanlsall).


### [Query parameters](#query-parameters-1)


- **pattern** (string) - Optional glob pattern.  Only pipeline names that match that pattern will be listed. If not supplied, the pattern defaults to `*` which matches everthing.


### [Response format detail](#response-format-detail-1)


**detail** is an array of strings.  Each string is the name of a pipeline.


#### [Sample Responses.](#sample-responses-1)


Rustogramer:


```json
{
    "status" : "Pipeline managment is not implemented - this is not SpecTcl",
    "detail": []
}

```


SpecTcl success:


```json
{
    "status" : "OK", 
    "detail" : [
        "raw-to-parameters",
        "filter"
    ]
}

```


SpecTcl failure gives a generic response:


```json
{
    "status" : "'pman ls' command failed",
    "detail" : "<Error message from the pman ls command>"
}

```


## [/spectcl/pman/current](#spectclpmancurrent)


Provide information about the currently selected event processor.


### [Query parameters](#query-parameters-2)


No query parameters are supported.


### [Response format detail](#response-format-detail-2)


**detail** is an object with attributes:


- **name** (string) - pipeline name.
- **processors** (array of strings) - Names of the processors in the current pipeline.  Note that the array element order is the same as the pipeline order.


#### [Sample Responses.](#sample-responses-2)


Rustogramer (Generic response):


```json
{
    "status" : "Pipeline management is not implemented",
    "detail" : "This is not SpecTcl",
}

```


SpecTcl success:


```json
{
    "status" "OK",
    "detail" {
        "name" : "raw-to-parameters", 
        "processors" : [
            "subsystem-1",
            "subsystem-2",
            "correlations",
            "computed-parameters"
        ]
    }
}

```


SpecTcl failure (Generic response):


```json
{
    "status" : "'pman current' command failed",
    "detail" : "<Error message from pman current command>"
}


```


## [/spectcl/pman/lsall](#spectclpmanlsall)


Provide detailed listings of event processing pipelines.


### [Query parameters](#query-parameters-3)


- **pattern** (string) - Optional glob pattern.  The event processors listed must have names that match the pattern.  If not provided, pattern defaults to `*` which matches everything.


### [Response format detail](#response-format-detail-3)


The **detail** is an array of objects.  Each object has the attributes:


- **name**  (string) - pipeline name.
- **processors** (array of strings) - Names of the event processors in the pipeline in the order in which they will be called.


#### [Sample Responses.](#sample-responses-3)


Rustogramer


```json
{
    "status" : "Pipeline management is not implemented - this is not SpecTcl",
    "detail" : []
}


SpecTcl success:

```json
{
    "status" : "OK", 
    "detail" : [
        {
            "name" : "raw",
            "processors" : [
                "subsystem-1",
                "subsystem-2",
                "correlations",
                "computed-parameters"
            ]
        },
        {
            "name" : "filter",
            "processors": [
                "filter-unpacker"
            ]
        }
    ]
}

```


## [/spectcl/pman/lsevp](#spectclpmanlsevp)


List the names of event processors.


### [Query parameters](#query-parameters-4)


- **pattern** (string) - Optional glob pattern.  Only event processors that match the pattern will be listed.


### [Response format detail](#response-format-detail-4)


**detail** is an array of strings that are the names of event processors.


#### [Sample Responses.](#sample-responses-4)


Rustogramer


```json
{
    "status" :  "Pipeline management is not implemented - this is not SpecTcl", 
    "detail" : []
}

```


Success from SpecTcl:


```json
{
    "status" : "OK",
    "detail" :  [
        "subsystem-1",
        "subsystem-2",
        "correlations",
        "computed-parameters",
        "filter-unpacker"
    ]
}

```


Failure from SpecTcl (generic response):


```json
{
    "status" : "'pman ls-evp' command failed",
    "detail" : "<error message from pman ls-evp command>"
}

```


## [/spectcl/pman/use](#spectclpmanuse)


Select the current event pipeline


### [Query parameters](#query-parameters-5)


- **name** (string) - Name of the event processing pipeline to make current.


### [Response format detail](#response-format-detail-5)


Generic response.


#### [Sample Responses.](#sample-responses-5)


Rustogramer:


```json
{
    "status" : "Pipeline management is not implemented",
    "detail" : "This is not SpecTcl"
}

```


SpecTcl success:


```json
{
    "status" : "OK"
}

```


SpecTcl Failure:


```json
{
    "status" : "'pman use' command failed",
    "detail" : "<error message from pman use>"
}

```


## [/spectcl/pman/add](#spectclpmanadd)


Adds a new event processor to an event processing pipeline.  The new processor is added to the end of the pipeline.
Note that if the pipeline being edited is current the effect on event processing is immediate.


### [Query parameters](#query-parameters-6)


- **pipeline** (string) - Mandatory name of the pipeline to be edited.
- **processor** (string) - Mandatory name of the event processor to append to the pipeline.  Note that a processor can be part of more than one pipeline of the application requires it.


### [Response format detail](#response-format-detail-6)


Generic response.


#### [Sample Responses.](#sample-responses-6)


Rustogramer:


```json
{
    "status": "Pipeline management is not implemented",
    "detail": "This is not SpecTcl"
}

```


SpecTcl success:


```json
{
    "status" : "OK"
}

```


SpecTcl Failure:


```json
{
    "status" : "pman 'add' command failed",
    "detail" : "<error message from pman add command>"
}

```


## [/spectcl/pman/rm](#spectclpmanrm)


Remove an event processor from a pipeline.  If the pipeline is currently in use, the effects on event processing are immediate.


### [Query parameters](#query-parameters-7)


- **pipeline** (string) - mandatory name of the pipeline to modify.
- **processor** (string) - mandatory name of the event processor to remove from the pipeline.


### [Response format detail](#response-format-detail-7)


The response is a generic response.


#### [Sample Responses.](#sample-responses-7)


Rustogramer:


```json
{
    "status": "Pipeline management is not implemented",
    "detail": "This is not SpecTcl"
}

```


SpecTcl success:


```json
{
    "status" : "OK"
}

```


SpecTcl Failure:


```json
{
    "status" : "'pman rm' command failed",
    "detail" : "<error message returned by pman rm command>"
}

```


## [/spectcl/pman/clear](#spectclpmanclear)


Removes all of the processors from an event processing pipeline.  If the pipeline is currently in use, the effect is immediate and could be disaastrous.


### [Query parameters](#query-parameters-8)


- **pipeline** (string) - Mandatory name of the pipeline to clear.


### [Response format detail](#response-format-detail-8)


Generates a generic response.


#### [Sample Responses.](#sample-responses-8)


Rustogramer:


```json
{
    "status": "Pipeline management is not implemented",
    "detail": "This is not SpecTcl"
}

```


SpecTcl success:


```json
{
    "status" : "OK"
}

```


SpecTcl Failure:


```json
{
    "status" : "'pman clear' command failed",
    "detail" : "<error message returned by pman clear command>"
}

```


## [/spectcl/pman/clone](#spectclpmanclone)


Sometimes it's useful to take an exising event processing pipeline as a starting point for a new one.  The clone request creates a new event processing pipeline that is a duplicate of an existing one.


### [Query parameters](#query-parameters-9)


- **source** (string) - Mandatory name of an existing pipeline to clone.
- **new** (string) - Name of a new pipeline to create that will be a duplicate  of the source.


### [Response format detail](#response-format-detail-9)


A generic response is produced.


#### [Sample Responses.](#sample-responses-9)


Rustogramer:


```json
{
    "status": "Pipeline management is not implemented",
    "detail": "This is not SpecTcl"
}

```


SpecTcl success:


```json
{
    "status" : "OK"
}

```


SpecTcl Failure:


```json
{
    "status" : "'pman clone' command failed",
    "detail" : "<error message returned by pman clone command>"
}

```




 Mobile navigation buttons 
[[chap7_2_mirror]]
[[chap7_2_project]]



[[chap7_2_mirror]]
[[chap7_2_project]]









 Custom JS scripts
