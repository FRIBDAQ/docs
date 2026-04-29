|  |  |  |
| --- | --- | --- |
| SpecTcl Sqlite3 interfaces |
| Prev |  | Next |


---

# <a name="AEN2742"></a>DBParameter

<a name="AEN2746"></a>## Name

DBParameter -- Encapsulate database parameter definitions.

<a name="AEN2749"></a>## Synopsis

```
#include <DBParameter.h>

namespace SpecTclDB {
    class SaveSet;
    
    class DBParameter {
    public:
        struct Info {
            int         s_id;
            int         s_savesetId;
            std::string s_name; 
            int         s_number;
            bool        s_haveMetadata;
            double      s_low;
            double      s_high;
            int         s_bins;
            std::string s_units;
        };
    public:
        static bool exists(CSqlite& connection, int sid, const char* name);
        static bool exists(CSqlite& connection, int sid, int id);
        
        static DBParameter* create(
            CSqlite& connection, int sid, const char* name, int number
        );
        static DBParameter* create(
            CSqlite& connection, int sid, const char* name, int number,
            double low, double high, int bins, const char* units
        );
        static DBParameter* get(CSqlite& connection, int sid, int id);
        static std::vector<DBParameter*> list(CSqlite& connection, int sid);
    public:
        DBParameter(CSqlite& conn, int saveid, const char* name);
        DBParameter(CSqlite& conn, int saveid, int number);

        const Info& getInfo();
        

        
    };
}                      
                    
```

<a name="AEN2751"></a>## DESCRIPTION

`SpecTclDB::DBParameter`
                        encapsulates the data in the database for
                        a single parameter definition.  It also
                        provides services that are related to parameters.

<a name="AEN2755"></a>## METHODS

Note that most methods described below require
                        that you have a database connection and the
                        primary key of a save set.  These methods are not
                        intended for general use but are used by
                        API methods for the parameter definitions in
                        `SpecTclDB::SaveSet` which
                        has these pieces of information available.



` static bool  exists(CSqlite&  connection = , int  sid  = , const char*  name = );`Determines if the parameter `name`
                                exists in the saveset with the
                                primary key `sid`
                                that is in the database with the connection
                                `conn`.
                                If the parameter exists, true
                                is returned, if not, false.
                                Note that if there are errors, they are signalled
                                by exceptions that are derived from
                                `std::exception`

` static bool  exists(CSqlite&  connection = , int  sid = , int  id = );`Same as the previous method but looks up the
                                parameter by its primary  key
                                `id`.

` static DBParameter*  create(CSqlite&  connection = , int  sid = , const char*  name  = , int  number = );`This method creates a new parameter definition
                                in the saveset with the primary key
                                `sid` in the
                                database `conn`.
                                The parameter is a primitive parameter that
                                only has a `name`
                                and `number`.

When the definition comes from SpecTcl, the
                                `number` is a slot in the
                                `CEvent` object where the unpacked
                                parameter will be stored.

The result is a pointer to a
                                new `SpecTclDB::DBParameter`
                                object that wraps the new definition.
                                The object is dynamically created so you
                                must delete it when your program no longer
                                needs it.

On errors like duplicate parameter name or
                                number or no such save set,
                                an `std::invalid_argument`
                                exception is thrown.  Other errors
                                result in exceptions that are derived from
                                `std::exception`.

` static DBParameter*  create(CSqlite&  connection = , int  sid = , const char*  name = ,  int  number = , double  low = , double  high = , int  bins = , const char*  units = );`Exactly like the previous method, however the
                                additional parameters supply the metadata
                                that is normally available in a tree parameter.
                                `low` is the
                                recommended axis low limit for axes that
                                defined on these parameters. `high`
                                is the recommended axis high limt for axes that are
                                defined on this parameter.
                                `bins`
                                is the recommended number of bins for axes
                                defined on this parameter using the
                                recommended limits.
                                `units` are the
                                units of measure of the parameter.
                                Note that for unitless parameters, by convention
                                an empty string is used.

` static DBParameter*  get(CSqlite&  connection = , int  sid = , int  id = );`Fetchs the parameter definition
                                with the primary key
                                `id` from
                                the saveset with a primary key of
                                `sid` from
                                the database connected via
                                `connection`.

If found, the parameter definition is
                                wrapped in
                                `SpecTclDB::DBParameter` object
                                and a pointer to that object is returned.
                                The object is dynamically created, therefore
                                when the program no longer needs it it must
                                be deleted

If the parameter does not exist,
                                `std::invalid_argument`
                                is thrown.

` static std::vector<DBParameter*>  list(CSqlite&  connection = , int  sid = );`Given a connection to a database
                                `connection` and the
                                primary key of a saveset,
                                `sid` lists all of the
                                parameter definitions that are in that saveset.
                                The result is a vector that contains pointers
                                to object wrappers for the data in the
                                database for each parameter.
                                These objects are dynamically generated and,
                                thereforem, must be deleted when no longer
                                needed by the program.

Any errors are reported as exceptions that are
                                derived from `std::exception`.

`  DBParameter(CSqlite&  conn = , int  saveid = , const char*  name = );`Looks up the parameter definition for
                                `name` and constructs
                                a `SpecTclDB::DBParameter`
                                object to wrap it.  `connection`
                                represents the connection to the database
                                and `sid` is the
                                primary key of the saveset the parameter
                                is defined in.

If there is no parameter named
                                `name` in the
                                designated save set
                                `SpecTclDB::invalid_argument`
                                is thrown.

`  DBParameter(CSqlite&  conn = , int  saveid = , int  number = );`This constructor locates the parameter definition
                                it wraps based on the parameter
                                `number`. The parameter
                                number is not the primary key of the parameter but
                                a number associated with the paramater name
                                when the definition is created. In the context of
                                SpecTcl, this number represents a slot in the
                                `CEvent` passed to
                                event processors into which the parameter will
                                be placed.

` const Info&  getInfo();`When a `SpecTclDB::DParameter`
                                is constructed, it fetches information about the
                                parameter from the database and caches it
                                internally in a
                                SpecTclDB::DBParameter::Info
                                struct.  This fetches a const reference to that
                                struct.

The members of the
                                SpecTclDB::DBParameter::Info are
                                described in DATA TYPES
                                below.

<a name="AEN2986"></a>## DATA TYPES

`SpecTclDB::DBParameter`
                        exports a single data type; Info
                        (fully qualified name SpecTclDB::DBParameter::Info).
                        This is a struct that is used to cache the database
                        definition of the parameter represented by instances
                        of `SpecTclDB::DBParameter`.

Info has the following fields:



int`s_id`The primary key of the database entry for
                                this parameter.

int`s_savesetId`A foreign key to the saveset that owns
                                the parameter.

std::string `s_name`The name of the parameter.

int`s_number`A number associated with the parameter.
                                For SpecTcl, this is the slot of the
                                `CEvent` passed to
                                event processors into which the parameter
                                value for an event will be placed.

bool`s_haveMetadata`Parameters in SpecTcl come in two flavors.
                                Raw parameters only have a number, the
                                index into `CEvent`
                                objects into which they get unpacked.
                                *Tree parameters*
                                also have metadata about the parameter.
                                This metadata, provides additional information
                                about the parameter.

If metadata is supplied for the parameter,
                                this flag will be true.
                                If not, this flag will be false.
                                The subsequent fields in
                                Info will only have valid values
                                if `s_haveMetadata`
                                is true.  If not those
                                fields should be ignored.

double `s_low`Metadata.  This is the lowest value expected
                                to be valid for the parameter.  It is a suggested
                                low limit of histogram axes that represent this
                                parameter.

double`s_high`Metadata.  This is the largest value expected to be
                                valid for this parameter.  It is a suggested
                                upper limit of histogram axes that
                                represent this parameter.

int`s_bins`Metadata.  This value says something about
                                the resolution with which the parameter is
                                represented. It recommends that if you
                                follow the axis limit suggestions provided
                                you parcel that axis out into
                                `s_bins` bins.

std::string `s_units`Metadata: This provides units of measure for the
                                parameter.  This and the
                                `s_name` field can
                                be used to derive axis labels for the parameter.
                                By convention, unitless parameters have
                                an empty string for this field.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| SaveSet | Up | DBSpectrum |
