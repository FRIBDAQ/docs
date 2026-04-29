<a name="AEN1"></a># <a name="AEN2"></a>SpecTcl Sqlite3 interfaces

### <a name="AEN4"></a>Ron Fox


---

- **Table of Contents**
- 1. [[Introduction|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c13.md]]
- 2. [[What you can do with the SpecTcl Sqlite database package.|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c36.md]]
- 3. [[C++ Low level API|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c65.md]]
  - 3.1. [[`SpecTclDB::CDatabase`|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c65.md#AEN108]]
  - 3.2. [[The SpecTclDB::SaveSet class.|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/x247.md]]
- 4. [[SpecTcl classes that record event data|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c597.md]]
  - 4.1. [[Lower layer of SpecTcl's event recording/playback code.|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c597.md#AEN606]]
  - 4.2. [[Upper layer of SpecTcl's event recording/playback code.|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/x748.md]]
- 5. [[Tcl bindings to the C++ API|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c755.md]]
- 6. [[SpecTcl API to the database.|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c1158.md]]
- 7. [[The SpecTcl database GUI.|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c1440.md]]
  - 7.1. [[The GUI Menubar|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c1440.md#AEN1471]]
  - 7.2. [[Pop Up context menus|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/x1521.md]]
- A. [[Reference material|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/a1577.md]]
  - A.1. [[Reference material for the C++ API classes.|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/a1577.md#AEN1579]]
    - [[CDatabase|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/r1582.md]] -- Database creation and access
    - [[SaveSet|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/r1682.md]] -- Encapsulate a save set.
    - [[DBParameter|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/r2742.md]] -- Encapsulate database parameter definitions.
    - [[DBSpectrum|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/r3061.md]] -- Encapsulate Spectrum definitions.
    - [[DBGate|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/r3375.md]] -- Encapsulate database gate definitions
    - [[DBApplication|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/r3817.md]] -- Wrap database definitions of gate applications
    - [[DBTreeVariable|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/r3961.md]] -- Ecapsulate tree variable definitions.
  - A.2. [[Object oriented Sqlite3 wrapper|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/x4153.md]]
    - [[CSqlite|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/r4187.md]] -- Connection to Sqlite3
    - [[CSqliteException|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/r4372.md]] -- Exception class for libsqlite3pp
    - [[CSqliteStatement|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/r4387.md]] -- Executes SQLite3 statements
    - [[CSqliteTransaction/CSqliteSavePoint|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/r4837.md]] -- Encapsulate Sqlite transactions/savepoints
    - [[CSqliteWhere|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/r5003.md]] -- Classes to build up WHERE clauses.
  - A.3. [[Tcl bindings to the C++ API|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/x5417.md]]
    - A.3.1. [[Raw Tcl API|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/x5417.md#AEN5434]]
    - A.3.2. [[SpecTcl API|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/x5417.md#AEN6030]]
    - A.3.3. [[Event recording API|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/x5417.md#AEN6318]]
  - A.4. [[Database schema.|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/x6432.md]]
    - A.4.1. [[Storing event data|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/x6432.md#AEN6778]]

- **List of Figures**
- 7-1. [[The SpecTcl database GUi window|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c1440.md#AEN1464]]

- **List of Examples**
- 3-1. [[Createing an empty database (makedb.cpp)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c65.md#AEN177]]
- 3-2. [[Creating savesets in a database (makesaveset.cpp)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c65.md#AEN196]]
- 3-3. [[Listing savesets (lssaveset.cpp)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c65.md#AEN220]]
- 3-4. [[Defining parameters (pardef.cpp)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/x247.md#AEN270]]
- 3-5. [[Defining Spectra (specdef.cpp)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/x247.md#AEN315]]
- 3-6. [[Defining gates (gatedef.cpp)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/x247.md#AEN378]]
- 3-7. [[Applying gates to spectra (applydef.cpp)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/x247.md#AEN427]]
- 3-8. [[Saving and recovering tree variables (vardef.cpp)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/x247.md#AEN451]]
- 3-9. [[Storing event data (evtstore.cpp)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/x247.md#AEN472]]
- 3-10. [[Recovering event data (evtget.cpp)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/x247.md#AEN519]]
- 3-11. [[Storing scaler readouts (sclstore.cpp)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/x247.md#AEN551]]
- 3-12. [[Recovering scaler readouts (sclget.cpp)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/x247.md#AEN565]]
- 5-1. [[Creating an empty database in Tcl (makedb.tcl)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c755.md#AEN778]]
- 5-2. [[Creating savesets in a database (makesaveset.tcl)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c755.md#AEN804]]
- 5-3. [[Listing savesets in a database (lssaveset.tcl)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c755.md#AEN837]]
- 5-4. [[Defining parameters (pardef.tcl)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c755.md#AEN846]]
- 5-5. [[Defining Spectra (specdef.tcl)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c755.md#AEN916]]
- 5-6. [[Defining gates (gatedef.tcl)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c755.md#AEN992]]
- 5-7. [[Applying gates to spectra (applydef.tcl)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c755.md#AEN1075]]
- 5-8. [[Saving and recovering tree variables (vardef.tcl)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c755.md#AEN1105]]
- 5-9. [[Storing spectrum contents (specstore.tcl)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c755.md#AEN1142]]
- 6-1. [[dbconfig - creating and connecting to a database|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c1158.md#AEN1172]]
- 7-1. [[Incorporating the database GUI in your SpecTcl|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/c1440.md#AEN1460]]
- A-1. [[How transactions are usually used|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/database/r4837.md#AEN4869]]

---

|  |  |  |
| --- | --- | --- |
|  |  | Next |
|  |  | Introduction |
