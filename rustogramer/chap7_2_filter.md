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
[[**|chap7_2_evbunpack]]
[[**|chap7_2_fit]]



[[**|chap7_2_evbunpack]]
[[**|chap7_2_fit]]









 Custom JS scripts
