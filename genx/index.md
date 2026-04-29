<a name="AEN1"></a># <a name="AEN2"></a>genx - system for framework independent analysis.

### <a name="AEN4"></a>Ron Fox


---

- **Table of Contents**
- 1. [[Introduction and motivation.|https://github.com/FRIBDAQ/docs/tree/main/genx/c13.md]]
- I. [[User manual|https://github.com/FRIBDAQ/docs/tree/main/genx/p31.md]]
  - 2. [[Writing data structure declaration files.|https://github.com/FRIBDAQ/docs/tree/main/genx/c43.md]]
  - 3. [[Translating structure declaration files into code for a target|https://github.com/FRIBDAQ/docs/tree/main/genx/c164.md]]
  - 4. [[Generated Code|https://github.com/FRIBDAQ/docs/tree/main/genx/c227.md]]
    - 4.1. [[Code Generated for SpecTcl|https://github.com/FRIBDAQ/docs/tree/main/genx/c227.md#AEN233]]
    - 4.2. [[Code generated for Root|https://github.com/FRIBDAQ/docs/tree/main/genx/x303.md]]
    - 4.3. [[Putting this all together for SpecTcl and Root.|https://github.com/FRIBDAQ/docs/tree/main/genx/x388.md]]
  - 5. [[Reference pages|https://github.com/FRIBDAQ/docs/tree/main/genx/c579.md]]
    - [[Genx Declaration language|https://github.com/FRIBDAQ/docs/tree/main/genx/r581.md]] -- Event definition language.
    - [[genx|https://github.com/FRIBDAQ/docs/tree/main/genx/r721.md]] -- Compiler for parameter definitions
- II. [[Programming manual|https://github.com/FRIBDAQ/docs/tree/main/genx/p759.md]]
  - 6. [[Adding a `--target` to the genx compiler.|https://github.com/FRIBDAQ/docs/tree/main/genx/c771.md]]
  - 7. [[Writing a generator|https://github.com/FRIBDAQ/docs/tree/main/genx/c805.md]]

- **List of Examples**
- 2-1. [[Data structure description file|https://github.com/FRIBDAQ/docs/tree/main/genx/c43.md#AEN49]]
- 3-1. [[Generating SpecTcl code from data.decl|https://github.com/FRIBDAQ/docs/tree/main/genx/c164.md#AEN195]]
- 3-2. [[Generating CERN/Root code from data.decl|https://github.com/FRIBDAQ/docs/tree/main/genx/c164.md#AEN201]]
- 4-1. [[Initialization of simple struct members for SpecTcl - the declaration|https://github.com/FRIBDAQ/docs/tree/main/genx/c227.md#AEN241]]
- 4-2. [[Initialization of simple struct members for SpecTcl - the header|https://github.com/FRIBDAQ/docs/tree/main/genx/c227.md#AEN245]]
- 4-3. [[Initialization of simple struct members for SpecTcl - the implementation|https://github.com/FRIBDAQ/docs/tree/main/genx/c227.md#AEN254]]
- 4-4. [[SpecTcl complex struct initialization - definition file:|https://github.com/FRIBDAQ/docs/tree/main/genx/c227.md#AEN264]]
- 4-5. [[SpecTcl complex struct initialization - header file|https://github.com/FRIBDAQ/docs/tree/main/genx/c227.md#AEN272]]
- 4-6. [[SpecTcl complex struct initialization - C++ file|https://github.com/FRIBDAQ/docs/tree/main/genx/c227.md#AEN277]]
- 4-7. [[Initialization code for SpecTcl - definition file|https://github.com/FRIBDAQ/docs/tree/main/genx/c227.md#AEN288]]
- 4-8. [[Initialization code for SpecTcl - header|https://github.com/FRIBDAQ/docs/tree/main/genx/c227.md#AEN292]]
- 4-9. [[Initialization code for SpecTcl - C++ file|https://github.com/FRIBDAQ/docs/tree/main/genx/c227.md#AEN299]]
- 4-10. [[Simple struct for Root - Declarations:|https://github.com/FRIBDAQ/docs/tree/main/genx/x303.md#AEN313]]
- 4-11. [[Simple struct for Root - Header|https://github.com/FRIBDAQ/docs/tree/main/genx/x303.md#AEN317]]
- 4-12. [[Simple struct for Root - C++ code|https://github.com/FRIBDAQ/docs/tree/main/genx/x303.md#AEN330]]
- 4-13. [[Complex data structure in Root, declaration|https://github.com/FRIBDAQ/docs/tree/main/genx/x303.md#AEN340]]
- 4-14. [[Complex data structure in Root, header|https://github.com/FRIBDAQ/docs/tree/main/genx/x303.md#AEN344]]
- 4-15. [[Complex data structure in Root, C++|https://github.com/FRIBDAQ/docs/tree/main/genx/x303.md#AEN348]]
- 4-16. [[Instances in Root - declaration file|https://github.com/FRIBDAQ/docs/tree/main/genx/x303.md#AEN352]]
- 4-17. [[Instances in root - header|https://github.com/FRIBDAQ/docs/tree/main/genx/x303.md#AEN356]]
- 4-18. [[Instances in root - C++|https://github.com/FRIBDAQ/docs/tree/main/genx/x303.md#AEN360]]
- 4-19. [[Initialize for Root:|https://github.com/FRIBDAQ/docs/tree/main/genx/x303.md#AEN370]]
- 4-20. [[CommitEvent for Root:|https://github.com/FRIBDAQ/docs/tree/main/genx/x303.md#AEN379]]
- 4-21. [[SetupEvent for Root:|https://github.com/FRIBDAQ/docs/tree/main/genx/x303.md#AEN385]]
- 4-22. [[event.decl - event declaration file for the example:|https://github.com/FRIBDAQ/docs/tree/main/genx/x388.md#AEN419]]
- 4-23. [[Makefile - generating code from event.decl|https://github.com/FRIBDAQ/docs/tree/main/genx/x388.md#AEN423]]
- 4-24. [[unpacker.cpp - example unpacker|https://github.com/FRIBDAQ/docs/tree/main/genx/x388.md#AEN429]]
- 4-25. [[SpecTcl/CUnpackerWrapper.h|https://github.com/FRIBDAQ/docs/tree/main/genx/x388.md#AEN452]]
- 4-26. [[SpecTcl/CUnpackerWrapper.cpp|https://github.com/FRIBDAQ/docs/tree/main/genx/x388.md#AEN460]]
- 4-27. [[SpecTcl/MySpecTclApp.cpp - AnalysisPipeline|https://github.com/FRIBDAQ/docs/tree/main/genx/x388.md#AEN466]]
- 4-28. [[SpecTcl/Makefile|https://github.com/FRIBDAQ/docs/tree/main/genx/x388.md#AEN472]]
- 4-29. [[Root/process.cpp modifications|https://github.com/FRIBDAQ/docs/tree/main/genx/x388.md#AEN502]]
- 4-30. [[Root/processor.cpp modifications|https://github.com/FRIBDAQ/docs/tree/main/genx/x388.md#AEN508]]
- 4-31. [[Root/Makefile|https://github.com/FRIBDAQ/docs/tree/main/genx/x388.md#AEN513]]
- 4-32. [[Full listing of TopLevel/event.decl|https://github.com/FRIBDAQ/docs/tree/main/genx/x388.md#AEN533]]
- 4-33. [[Full listing of TopLevel/Makefile|https://github.com/FRIBDAQ/docs/tree/main/genx/x388.md#AEN537]]
- 4-34. [[Full listing of TopLevel/unpacker.cpp|https://github.com/FRIBDAQ/docs/tree/main/genx/x388.md#AEN541]]
- 4-35. [[TopLevel/SpecTcl/CUnpackerWrapper.h|https://github.com/FRIBDAQ/docs/tree/main/genx/x388.md#AEN548]]
- 4-36. [[TopLevel/Spectcl/CUnpackerWrapper.cpp|https://github.com/FRIBDAQ/docs/tree/main/genx/x388.md#AEN552]]
- 4-37. [[TopLevel/SpecTcl/MySpecTclApp.cpp (comments removed)|https://github.com/FRIBDAQ/docs/tree/main/genx/x388.md#AEN556]]
- 4-38. [[TopLevel/SpecTcl/Makefile|https://github.com/FRIBDAQ/docs/tree/main/genx/x388.md#AEN560]]
- 4-39. [[TopLevel/Root/process.cpp|https://github.com/FRIBDAQ/docs/tree/main/genx/x388.md#AEN567]]
- 4-40. [[TopLevel/Root/processor.cpp (comments removed)|https://github.com/FRIBDAQ/docs/tree/main/genx/x388.md#AEN571]]
- 4-41. [[TopLevel/Root/Makefile|https://github.com/FRIBDAQ/docs/tree/main/genx/x388.md#AEN575]]

---

|  |  |  |
| --- | --- | --- |
|  |  | Next |
|  |  | Introduction and motivation. |
