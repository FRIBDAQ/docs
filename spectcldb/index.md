<a name="AEN1"></a># <a name="AEN2"></a>SpecTcl Sqlite3 interfaces

### <a name="AEN4"></a>Ron Fox


---

- **Table of Contents**
- 1. [[Introduction|c13]]
- 2. [[What you can do with the SpecTcl Sqlite database package.|c36]]
- 3. [[C++ Low level API|c65]]
  - 3.1. [[`SpecTclDB::CDatabase`|c65#AEN108]]
  - 3.2. [[The SpecTclDB::SaveSet class.|x247]]
- 4. [[SpecTcl classes that record event data|c597]]
  - 4.1. [[Lower layer of SpecTcl's event recording/playback code.|c597#AEN606]]
  - 4.2. [[Upper layer of SpecTcl's event recording/playback code.|x748]]
- 5. [[Tcl bindings to the C++ API|c755]]
- 6. [[SpecTcl API to the database.|c1158]]
- 7. [[The SpecTcl database GUI.|c1440]]
  - 7.1. [[The GUI Menubar|c1440#AEN1471]]
  - 7.2. [[Pop Up context menus|x1521]]
- A. [[Reference material|a1577]]
  - A.1. [[Reference material for the C++ API classes.|a1577#AEN1579]]
    - [[CDatabase|r1582]] -- Database creation and access
    - [[SaveSet|r1682]] -- Encapsulate a save set.
    - [[DBParameter|r2742]] -- Encapsulate database parameter definitions.
    - [[DBSpectrum|r3061]] -- Encapsulate Spectrum definitions.
    - [[DBGate|r3375]] -- Encapsulate database gate definitions
    - [[DBApplication|r3817]] -- Wrap database definitions of gate applications
    - [[DBTreeVariable|r3961]] -- Ecapsulate tree variable definitions.
  - A.2. [[Object oriented Sqlite3 wrapper|x4153]]
    - [[CSqlite|r4187]] -- Connection to Sqlite3
    - [[CSqliteException|r4372]] -- Exception class for libsqlite3pp
    - [[CSqliteStatement|r4387]] -- Executes SQLite3 statements
    - [[CSqliteTransaction/CSqliteSavePoint|r4837]] -- Encapsulate Sqlite transactions/savepoints
    - [[CSqliteWhere|r5003]] -- Classes to build up WHERE clauses.
  - A.3. [[Tcl bindings to the C++ API|x5417]]
    - A.3.1. [[Raw Tcl API|x5417#AEN5434]]
    - A.3.2. [[SpecTcl API|x5417#AEN6030]]
    - A.3.3. [[Event recording API|x5417#AEN6318]]
  - A.4. [[Database schema.|x6432]]
    - A.4.1. [[Storing event data|x6432#AEN6778]]

- **List of Figures**
- 7-1. [[The SpecTcl database GUi window|c1440#AEN1464]]

- **List of Examples**
- 3-1. [[Createing an empty database (makedb.cpp)|c65#AEN177]]
- 3-2. [[Creating savesets in a database (makesaveset.cpp)|c65#AEN196]]
- 3-3. [[Listing savesets (lssaveset.cpp)|c65#AEN220]]
- 3-4. [[Defining parameters (pardef.cpp)|x247#AEN270]]
- 3-5. [[Defining Spectra (specdef.cpp)|x247#AEN315]]
- 3-6. [[Defining gates (gatedef.cpp)|x247#AEN378]]
- 3-7. [[Applying gates to spectra (applydef.cpp)|x247#AEN427]]
- 3-8. [[Saving and recovering tree variables (vardef.cpp)|x247#AEN451]]
- 3-9. [[Storing event data (evtstore.cpp)|x247#AEN472]]
- 3-10. [[Recovering event data (evtget.cpp)|x247#AEN519]]
- 3-11. [[Storing scaler readouts (sclstore.cpp)|x247#AEN551]]
- 3-12. [[Recovering scaler readouts (sclget.cpp)|x247#AEN565]]
- 5-1. [[Creating an empty database in Tcl (makedb.tcl)|c755#AEN778]]
- 5-2. [[Creating savesets in a database (makesaveset.tcl)|c755#AEN804]]
- 5-3. [[Listing savesets in a database (lssaveset.tcl)|c755#AEN837]]
- 5-4. [[Defining parameters (pardef.tcl)|c755#AEN846]]
- 5-5. [[Defining Spectra (specdef.tcl)|c755#AEN916]]
- 5-6. [[Defining gates (gatedef.tcl)|c755#AEN992]]
- 5-7. [[Applying gates to spectra (applydef.tcl)|c755#AEN1075]]
- 5-8. [[Saving and recovering tree variables (vardef.tcl)|c755#AEN1105]]
- 5-9. [[Storing spectrum contents (specstore.tcl)|c755#AEN1142]]
- 6-1. [[dbconfig - creating and connecting to a database|c1158#AEN1172]]
- 7-1. [[Incorporating the database GUI in your SpecTcl|c1440#AEN1460]]
- A-1. [[How transactions are usually used|r4837#AEN4869]]

---

|  |  |  |
| --- | --- | --- |
|  |  | Next |
|  |  | Introduction |
