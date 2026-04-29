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

# [/spectcl/filter requests](#spectclfilter-requests)


SpecTcl filters output a reduced data set given an input set.  The output set is self-descsribing and can contain a limited parameters set as well as events that only make a specific gate true.


This domain of URIs is only supported by SpecTcl.  If attempted with Rustogramer, Generic responses of the form:


```json
{
    "status" : "/spectcl/filter/<specific> is not implemented",
    "detail" : "This is not SpecTcl"
}

```


Are returned where `<specific>` is the specific request and is one of:


- [`new`](#spectclfilternew) - Which SpecTcl uses to create a new filter.
- [`delete`](#spectclfilterdelete) - which delets an existing filter.
- [`enable`](#spectclfilterenable) - which enables an existing filter to write it's subset of data for future events.
- [`disable`](#spectclfilterdisable) - which disables an existing filter so that it will no longher write events.
- [`regate`](#spectclfilterregate) - which associates a different gate with an existing filter, changing the subset of events that will be written by the filter (when enabled).
- [`file`](#spectclfilterfile) - Which specifies a file on which filtered data will be written.
- [`list`](#spectclfilterlist) - which lists filters and their properties.
- [`format`](#spectclfilterformat) - which specifies an output format for a filter.


This family of URIs is a front end to the SpecTcl **filter** command documented in the
[SpecTcl command reference](https://docs.nscl.msu.edu/daq/newsite/spectcl-5.0/cmdref/index.html)


## [/spectcl/filter/new](#spectclfilternew)


Creates a new filter.  The filter is not associated with a file and cannot be enabled until it is.


### [Query parameters](#query-parameters)


- **name** (string) - Mandatory Name to be given to the new filter.
- **gate** (string) - name of a gate that will select the events the filter will write whne it is enabled.
- **parameter** (string) - In general this occurs several times, once for each parameter you wish written by the filter.


For example:


```
.../spectcl/filter/create?name=afilter&gate=alpha&parameter=alpha.energy&parameter=alpha.theta&parameter=alphas.phi&parameter=total.energy

```


Attempts to create a filter named `afilter` that will write events that make `alpha` true and will write the parameters
`alpha.energy`, `alpha.theta`, `alpha.phi` and `total.energy`


### [Response format detail](#response-format-detail)


The response is a generic respones.


#### [Sample Responses.](#sample-responses)


Succesful request:


```json
{
    "status" : "ok"
}

```


Request that is missing a gate:


```json
{
    "status" : "Missing required query parameter: ",
    "detail" : "gate"
}

```


## [/spectcl/filter/delete](#spectclfilterdelete)


Deletes a filter. Any open filter file is flushed and closed.


### [Query parameters](#query-parameters-1)


- **name** (string) - Mandatory name of a filter to delete.


### [Response format detail](#response-format-detail-1)


Rsponses are generic responses.


#### [Sample Responses.](#sample-responses-1)


Successful completion:


```json
{
    "status" : "OK"
}

```


Failure:


```json
{
    "status" :  "'filter -delete' command failed",
    "detail" : "<error message from the fileter -delete command>"
}

## /spectcl/filter/enable

Enable a filter.   Note that the filter must have a file associated with it for this to succeed.  Filters are created in the disabled state.  Once enabled, on subsequent events that make their gates true, they will write filtered data to file.

### Query parameters

* **name** (string) - mandtory filter name.

### Response format detail

Response is a generic response.


#### Sample Responses.

Success:
```json
{
    "status" : "OK"
}

```


Falure form:


```json
{
    "status" : "'filter -enable' command failed" 
    "detail" : "<Error message from SpecTcl filter commnand>"
}

```


## [/spectcl/filter/enable](#spectclfilterenable)


Enables a filter to write events.  Once a file has been associated with a filter it can be enabled to write events to that file. See also [/disable](#spectclfilterdisable)


### [Query parameters](#query-parameters-2)


- **name** (string) - mandatory parameter - the name of the filter to enable.


### [Response format detail](#response-format-detail-2)


Generic response.


#### [Sample Responses.](#sample-responses-2)


Success:


```json
{
    "status" : "OK"
}

```


Failure:


```json
{
    "status" : "'filter command' command failed" ,
    "detail" : "<error message from filter command>"
}

```


## [/spectcl/filter/disable](#spectclfilterdisable)


THe filter specified flushes any buffered data to its output file; and no longer writes data unless it is later enabled without changing the output file.


### [Query parameters](#query-parameters-3)


- **name** (string) - mandatory parameter specifies the filter.


### [Response format detail](#response-format-detail-3)


Generic format.


#### [Sample Responses.](#sample-responses-3)


Success:


```json
{
    "status" : "OK"
}

```


Failure:


```json
{
    "status" : "'filter -disable' command failed" ,
    "detail" : "<error message from filter command>"
}

```


## [/spectcl/filter/regate](#spectclfilterregate)


Changes the gate that determines which event are written to the filter.  Note as well that the filter will also dynamically reflects edits to its gate.


### [Query parameters](#query-parameters-4)


- **name** (string) - mandatory parameter that specifies the filter to modify.
- **gate** (string) - mandatory parameter that specifies a new gate for the filter. While odd, it is not an error to specify the current gate.


### [Response format detail](#response-format-detail-4)


Generic reply.


#### [Sample Responses.](#sample-responses-4)


Success:


```json
{
    "status" : "OK"
}

```


Failure:


```json
{
    "status" : "'filter -regate' command failed" ,
    "detail" : "<error message from filter command>"
}

```


## [/spectcl/filter/file](#spectclfilterfile)


Sets the filter output file.  Note that any existing file is first closed.


### [Query parameters](#query-parameters-5)


- **name** (string) - mandatory name of the filter.
- **file** (string) - mandatory path to the new output file:
  - **file** is interpreted by SpecTcl an therefore must be a valid file path in the context of the server.
  - If **file** exists, it will be ovewritten.
  - A file must have been specified for a filter for it to be legally enabled.


### [Response format detail](#response-format-detail-5)


Generic response.


#### [Sample Responses.](#sample-responses-5)


Success:


```json
{
    "status" : "OK"
}

```


Failure:


```json
{
    "status" : "'filter -file' command failed" ,
    "detail" : "<error message from filter command>"
}

```


## [/spectcl/filter/list](#spectclfilterlist)


Lists filters and their properties.


### [Query parameters](#query-parameters-6)


- **pattern** (string) - Optional glob pattern. Only filters with names that match **pattern** will be included in the listing.  If omitted the pattern defaults to `*` which matches all filters.


### [Response format detail](#response-format-detail-6)


**detail** is an array of objects. The objects have the followig fields:


- **name** (string) - Name of the filter being desribed.
- **gate** (string) - Name of the gate applied to the filter.
- **file** (string) - File to which the filter writes its events. This could be an empty string if the filters is not yet associated with a file.
- **parameters** (array of strings) - Name of the parameters written to the filter for each event it writes.
- **enabled** (string) - Either `enabled` or `disabled` depending on the filter enabled status.
- **format** (string) - The format with which the filter is written. See [format](#spectclfilterformat) for more information about this.


#### [Sample Responses.](#sample-responses-6)


Success - with a single filter:


```json
{
    "status" : "OK",
    "detail" : [
        {
            "name" : "afilter",
            "gate" : "agate",
            "file" : "/home/ron/filterile.flt",
            "parameters" : [
                "param1",
                "param2",
                "param3"
            ],
            "enabled": "enabled",
            "format" : "xdr"
        }
    ]
}

```


This can only fail if **pattern** is an illegal glob pattern.


## [/spectcl/filter/format](#spectclfilterformat)


Sets the format of the filter output. By default this is `xdr`, which is the built in filter file format.  The set of filter file formats can be extended.  This is described in the section `Extending SpecTcl's filter file format` in the [SpecTcl Programming Guide](https://docs.nscl.msu.edu/daq/newsite/spectcl-5.0/pgmguide/index.html).


The format of the built in `xdr` filter format [is described here](https://docs.nscl.msu.edu/daq/spectcl/Programming/filterread.htm). Scroll down to the section `Structure of a Filtered event file.`


### [Query parameters](#query-parameters-7)


- **name** (string) - mandatory name of the filter to modify.
- **format** (string) - mandatory format selector.


### [Response format detail](#response-format-detail-7)


This is a Generic response.


#### [Sample Responses.](#sample-responses-7)


Success:


```json
{
    "status": "OK"
}

```


Failure:


```json
{
    "status" : "'filter -format' command failed" ,
    "detail" : "<error message from filter command>"
}

```




 Mobile navigation buttons 
[[chap7_2_evbunpack]]
[[chap7_2_fit]]



[[chap7_2_evbunpack]]
[[chap7_2_fit]]









 Custom JS scripts
