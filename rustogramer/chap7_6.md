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

# [Schema of configuration files](#schema-of-configuration-files)


Configuration files are saved by rustogramer in Sqlite3 databases.  Sqlite3 data bases are a single file relational database.  SpecTcl and Rustogramer are both able to recover the analysis configuration from these database files.


This section documents the database schema of those files.  Note that [SpecTcl schema additions](#spectcl-schema-additions) describes the section of the scheme that is only used by SpecTcl.


This section assumes that you have a basic understanding of relational databases.


In this database schema table primary keys are an integer field named `id`.  The values of these primary keys are used as foreign keys to link tables together.


### [Save Sets](#save-sets)


The database format provides support for storing several configurations.  This is not curruently used by rustogramer or SpecTcl.   Each configuration is called a *save set* and the top level table for a configuration is
the *save_set* table which is generated using the following database definition language (DDL)


```sql
 CREATE TABLE IF NOT EXISTS  save_sets 
                (id  INTEGER PRIMARY KEY,
                name TEXT UNIQUE,
                timestamp INTEGER)

```


The table has the following fields:


- *id* - the primary key of the row.  Used to associated rows in other tables with specific save sets.
- *name* - name of the save set.  When the rustogramer GUI is used to save/restore the configuration the save-set created is called `rustogramer_gui`.
- *timestamp* - Is the system timestamp that identifies when the table was created.  For savesets generated by the Rustogramer GUI, this is given the value from the Python `time.time()` function.


### [Parameter definitions](#parameter-definitions)


Parameter definitions are relatively simple and require only a single table that is created using the following DDL


```sql
CREATE TABLE IF NOT EXISTS parameter_defs
                (id      INTEGER PRIMARY KEY,                    
                save_id INTEGER NOT NULL,  -- foreign key to save_sets.id
                name    TEXT NOT NULL,
                number  INTEGER NOT NULL,
                low     REAL,
                high    REAL,
                bins    INTEGER,
                units   TEXT)

```


The fields in this table are:


- *id* - Primary key.  Tables which refer to parameter definitions will use this as the foreign key.
- *save_id - Foreign key to the [save_sets](#save-sets) table.  This is the value of the primary key of the row in that table that identifies which save set this parmaeter definition belongs to.
- *name* - Name of the parameter.
- *number* - Parameter id used internally to SpecTcl and Rustogramer's histograming engines.
- *low* - Suggested low axis limit
- *high* - Suggested high axis limit.
- *bins* - Suggested number of axis bins.
- *units* - Units of measure of the parameter.


Clearly there will be one row in this table for each parameter definition.


### [Spectrum definitions.](#spectrum-definitions)


Several tables are required for each spectrum definition.  This is because each table has several parameters and may have several axes


The *root* table for spectrum defintions is *spectrum_defs* which is defined as follows:


```sql
CREATE TABLE IF NOT EXISTS spectrum_defs
                (id      INTEGER PRIMARY KEY,
                save_id INTEGER NOT NULL,     -- Foreign key to save_sets.id
                name    TEXT NOT NULL,
                type    TEXT NOT NULL,
                datatype TEXT NOT NULL
            )

```


- *id* - is the row's primary key.  Parts of the definition in other tables that refer to this spectrum will have the row's primary key as a foreign key.
- *save_id* - is a foreign key into the [save_sets](#save-sets) table. This identifies which save set this definition belongs to.
- *name* - is the name of the spectrum being defined.
- *type* - is the textual type of the spectrum being defined.
- *datatype* - is the bin data-type of the spectrum being defined.  Note that when recovering configuration written by e.g. Rustogramer in SpecTcl (or the other way around), the restoration code may not honor this datatype as the set of bin datatypes supported by the two programs is disjoint (f64 for rustogramer, and long, short, byte for SpecTcl).


#### [axis_defs](#axis_defs)


This table contains axis defintions.  In restoring a spectrum from the configuration, the assumpption is made that the primary keys are chronologically monotonic, in that case, with the X axis saved first then the Y axis, fetching the axis definitions sorted by primary key allows us to distinguish between the X and Y axis definitions.
The *axis_defs* table is defined using the following DDL:


```sql
CREATE TABLE IF NOT EXISTS axis_defs
            (
                id           INTEGER PRIMARY KEY,
                spectrum_id  INTEGER NOT NULL,  -- FK to spectrum_defs.id
                low          REAL NOT NULL,
                high         REAL NOT NULL,
                bins         INTEGER NOT NULL
            )

```


- *id* - is the primary key of the row.
- *spectrum_id* is a foreign key into the [spectrum_defs](#spectrum-definitions) table indicating which spectrum this axis belongs to.  In a spectrum with two axes, as desdribed above, the one with the smaller value for *id* will be the X axis.
- *low* - Axis low limit.
- *high* - Axis high limit.
- *bins* number of bins on the axis.


#### [Spectrum parameters.](#spectrum-parameters)


The set of tables that describe the spectrum parameters reflect the evolution of spectrum types. For the most part the *spectrum_params* table should not be used, in favor of the *spectrum_x_params* and *spectrum_y_params.  Even so, capturing the parameters required by a gamma summary spectrum is not clear and probably additional scheme will need to be added to adequatly handle this.  All three tables, have the same scheme, so we'll only show the *spectrum_params* table definition:


```sql
 CREATE TABLE IF NOT EXISTS spectrum_params   
            (   id          INTEGER PRIMARY KEY,          
                spectrum_id INTEGER NOT NULL,             
                parameter_id INTEGER NOT NULL             
            )

```


- *id* - is the primary key of a row in this table.
- *spectrum_id* is a foreign key from [spectrum_defs](#spectrum-definitions) wich indicates the spectrum this parameter belongs to.
- *parameter_id* is a foreign key from [parameter_defs](#parameter-definitions) indicating the parameter.


To give an idea of how this all hangs together, here's SQL that can grab the names of the X parameters required by the spectrum:


```sql
SELECT spectrum_defs.name, parameter_defs.name FROM spectrum_x_params
    INNER JOIN parameter_defs ON spectrum_x_params.parameter_id = parameter_defs.id
    INNER JOIN spectrum_defs ON  spectrum_x_params.spectrum_id  = spectrum_defs.id
    WHERE spectrum_defs.save_id = :saveset  
        AND spectrum_defs.name  =  :spectrum

```


Where


- :saveset - is a saved query parameter that is the save set id.
- :spectrum  -is a saved query parameter that is the name of a specturm.


Note how the joins are used to link the rows in the *spectrum_x_params* tables to the [spectrum_defs](#spectrum-definitions) and [parameter_defs](#parameter-definitions) tables via the foreign keys in *spectrum_x_params*


### [Condition definitions](#condition-definitions)


Condition (gate) definitions are the most complex schema in this database.  However, in general for a given condition type, only a very small subset of the schema is required.


The top level, or root table for condition definitions is *gate_defs*:


```sql
CREATE TABLE IF NOT EXISTS gate_defs       
                (   id          INTEGER PRIMARY KEY,   
                    saveset_id  INTEGER NOT NULL,      
                    name        TEXT NOT NULL,         
                    type        TEXT NOT NULL          
                )

```


- *id* - is the gate definition primary key.  This is a foreign key in all of the remaining tables in the Gate schema, tying rows back to the specific condition they describe.
- *saveset_id* - Foreign key from [save_sets](#save-sets) indicating the save set this definition belongw to.
- *name* - name of the condition.
- *type* - condition type code.


#### [Condition points](#condition-points)


Conditions that are geometric in 1-d or 2-d use this table to store the coordinates of their points.  The points are ordered by the primary key assigned to  each point row.  The table is defined as:


```sql
CREATE TABLE IF NOT EXISTS gate_points  
    (   id          INTEGER PRIMARY KEY,   
        gate_id     INTEGER NOT NULL,      
        x           REAL,                  
        y           REAL                   
    )

```


- *id* - is the primary key of the point.
- *gate_id* is a foreign key that contains the primary key of the row in the [gate_defs](#condition-definitions) table of the gate this point belongs to.
- *x*, *y*  - are the coordinates of a point.  In the case of a 1-d gate (e.g. a slice), only the *x* coordinate is used and the first point is the low limit, the second the high limit of the acceptance region.


#### [Condition parameters](#condition-parameters)


Conditions that depend on parameters, store their parameters here:


```sql
CREATE TABLE IF NOT EXISTS gate_parameters 
    (   id   INTEGER PRIMARY KEY,           
        parent_gate INTEGER NOT NULL,       
        parameter_id INTEGER NOT NULL       
    )

```


- *id* the primary key of the row.
- *parent_gate* - A foreign key that identifies which gate in [gate_defs](#condition-definitions) this parameter belongs to.
- *parameter_id - A foreign key that identifies which parameter in [parameter_defs](#parameter-definitions) this parameter identifies.


#### [Condition dependent gates](#condition-dependent-gates)


Compound conditions, depend on other previously defined condtions. This table provides the conditions a condition dpeends on:


```sql
 CREATE TABLE IF NOT EXISTS component_gates       
    (                                            
        id          INTEGER PRIMARY KEY,         
        parent_gate INTEGER NOT NULL,           
        child_gate  INTEGER NOT NULL            
    )

```


- *id* - the row's primary key.
- *parent_gate* - A foreign key into [gate_defs](#condition-definitions) identifying which condition, this condition is a component of.
- *child_gate* - A foreign key into [gate_defs](#condition-definitions) identifying a condition the condition indicated by *parent_gate* depends on.


#### [Condition bit masks](#condition-bit-masks)


Bit mask conditions, supported by SpecTcl require storage of their bitmask:


```sql
CREATE TABLE IF NOT EXISTS gate_masks    
    (   id          INTEGER PRIMARY KEY,     
        parent_gate INTEGER NOT NULL,        
        mask        INTEGER NOT NULL         
    )

```


- *id* - primary key of the row.
- *parent_gate* - foreign key  in [gate_defs](#condition-definitions) identifying which condition this mask belongs to.
- *mask* - The bit mask itself.


### [Gate applications](#gate-applications)


Conditions can be applied to spectra at which  point they become a gate to that spectrum.  This is captured as shown below:


```sql
CREATE TABLE IF NOT EXISTS gate_applications 
    (
        id                INTEGER PRIMARY KEY,  
        spectrum_id       INTEGER NOT NULL,     
        gate_id           INTEGER NOT NULL      
    )

```


Where


- *id* - is the row primary key.
- *spectrum_id* is a foreign key into [spectrum_defs](#spectrum-definitions) indicating the spectrum that is being gated.
- *gate_id* is a foreign key into [gate_defs](#condition-definitions) indicating which condition is the gate.


## [SpecTcl Schema Additions](#spectcl-schema-additions)


SpecTcl implements treevariables which are not implemented, nor needed by Rustogramer.  To support this, the schema also has the following table which is empty when a configuration is saved by rustogramer:


```sql
CREATE TABLE IF NOT EXISTS treevariables 
    (   
        id             INTEGER PRIMARY KEY,   
        save_id        INTEGER NOT NULL,      
        name           TEXT NOT NULL,         
        value          DOUBLE NOT NULL,       
        units          TEXT                   
    )

```


- *id* - is the row primary key.
- *save_id* is a foreign key to [save_sets](#save-sets) which indicates the save set that this definition belongs to.
- *name* - is the name of a tree variable.
- *value* - nIs the value of the variable.
- *units* - is the units of measure of the variable.


## [Bindset Schema additions](#bindset-schema-additions)


The python gui will create and populate a schema to save and restore the bindsets it knows
about.  SpecTcl, directly does not do that.  The Python GUI load operations can detect the
lack of the tables descsribed below and operate accordingly.


Two tables are required to save bindsets.  The first one, stores the name and description.
The second the spectra in each bindset:


```sql
CREATE TABLE IF NOT EXISTS binding_sets (
    id            INTEGER PRIMARY KEY,
    save_id       INTEGER NOT NULL,    -- FK save set id.
    name          TEXT NOT NULL,
    description   TEXT DEFAULT NULL
)

```


Where:


- *id* is the row's primary key and is used as a foreign key to identify the bindset.
- *save_id* is the id of the save set this binding set belongs to.
- *name* is the name of the binding set.
- *description* is a longer description of the binding set.


Spectra in a binding set are stored in:


```sql
CREATE TABLE IF NOT EXISTS bound_spectra (
    id    INTEGER PRIMARY KEY,
    bindset_id INTEGER NOT NULL, -- FK to binding_sets which set.
    spectrum_id INTEGER NOT NULL -- FK to spectrum_defs spectrum in binding set.
)

```


- *id*  is the primary key of the bound spectrum.
- *bindset_id*  is a foreign key containing the primary key of the binding_set in which the
  spectrum lives (from binding_sets).
- *spectrum_id* is a foreign key from spectrum_defs containing the primary key of the spectrum
  that is a member of the binding set.


For exsample, given a binding set name, the following query returns the names of all spectra
that are in that binding set:


```sql
SELECT spectrum_defs.name FROM spectrum_defs
    INNER JOIN bound_spectra on spectrum_defs.id = bound_spectra.spectrum_id
    INNER JOIN binding_sets on binding_sets.id = bound_spectra.bindset_id
    WHERE binding_sets.name = :bset_name

```


In the query above, `:bset_name` is a bound parameter of the query that will be substituted
at run-time.




 Mobile navigation buttons 
[[**|chap7_5]]
[[**|chap7_7]]



[[**|chap7_5]]
[[**|chap7_7]]









 Custom JS scripts
