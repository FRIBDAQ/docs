<a name="AEN1"></a># <a name="AEN2"></a>genx - system for framework independent analysis.

### <a name="AEN4"></a>Ron Fox


---

- **Table of Contents**
- 1. [[Introduction and motivation.|c13]]
- I. [[User manual|p31]]
  - 2. [[Writing data structure declaration files.|c43]]
  - 3. [[Translating structure declaration files into code for a target|c164]]
  - 4. [[Generated Code|c227]]
    - 4.1. [[Code Generated for SpecTcl|c227#AEN233]]
    - 4.2. [[Code generated for Root|x303]]
    - 4.3. [[Putting this all together for SpecTcl and Root.|x388]]
  - 5. [[Reference pages|c579]]
    - [[Genx Declaration language|r581]] -- Event definition language.
    - [[genx|r721]] -- Compiler for parameter definitions
- II. [[Programming manual|p759]]
  - 6. [[Adding a `--target` to the genx compiler.|c771]]
  - 7. [[Writing a generator|c805]]

- **List of Examples**
- 2-1. [[Data structure description file|c43#AEN49]]
- 3-1. [[Generating SpecTcl code from data.decl|c164#AEN195]]
- 3-2. [[Generating CERN/Root code from data.decl|c164#AEN201]]
- 4-1. [[Initialization of simple struct members for SpecTcl - the declaration|c227#AEN241]]
- 4-2. [[Initialization of simple struct members for SpecTcl - the header|c227#AEN245]]
- 4-3. [[Initialization of simple struct members for SpecTcl - the implementation|c227#AEN254]]
- 4-4. [[SpecTcl complex struct initialization - definition file:|c227#AEN264]]
- 4-5. [[SpecTcl complex struct initialization - header file|c227#AEN272]]
- 4-6. [[SpecTcl complex struct initialization - C++ file|c227#AEN277]]
- 4-7. [[Initialization code for SpecTcl - definition file|c227#AEN288]]
- 4-8. [[Initialization code for SpecTcl - header|c227#AEN292]]
- 4-9. [[Initialization code for SpecTcl - C++ file|c227#AEN299]]
- 4-10. [[Simple struct for Root - Declarations:|x303#AEN313]]
- 4-11. [[Simple struct for Root - Header|x303#AEN317]]
- 4-12. [[Simple struct for Root - C++ code|x303#AEN330]]
- 4-13. [[Complex data structure in Root, declaration|x303#AEN340]]
- 4-14. [[Complex data structure in Root, header|x303#AEN344]]
- 4-15. [[Complex data structure in Root, C++|x303#AEN348]]
- 4-16. [[Instances in Root - declaration file|x303#AEN352]]
- 4-17. [[Instances in root - header|x303#AEN356]]
- 4-18. [[Instances in root - C++|x303#AEN360]]
- 4-19. [[Initialize for Root:|x303#AEN370]]
- 4-20. [[CommitEvent for Root:|x303#AEN379]]
- 4-21. [[SetupEvent for Root:|x303#AEN385]]
- 4-22. [[event.decl - event declaration file for the example:|x388#AEN419]]
- 4-23. [[Makefile - generating code from event.decl|x388#AEN423]]
- 4-24. [[unpacker.cpp - example unpacker|x388#AEN429]]
- 4-25. [[SpecTcl/CUnpackerWrapper.h|x388#AEN452]]
- 4-26. [[SpecTcl/CUnpackerWrapper.cpp|x388#AEN460]]
- 4-27. [[SpecTcl/MySpecTclApp.cpp - AnalysisPipeline|x388#AEN466]]
- 4-28. [[SpecTcl/Makefile|x388#AEN472]]
- 4-29. [[Root/process.cpp modifications|x388#AEN502]]
- 4-30. [[Root/processor.cpp modifications|x388#AEN508]]
- 4-31. [[Root/Makefile|x388#AEN513]]
- 4-32. [[Full listing of TopLevel/event.decl|x388#AEN533]]
- 4-33. [[Full listing of TopLevel/Makefile|x388#AEN537]]
- 4-34. [[Full listing of TopLevel/unpacker.cpp|x388#AEN541]]
- 4-35. [[TopLevel/SpecTcl/CUnpackerWrapper.h|x388#AEN548]]
- 4-36. [[TopLevel/Spectcl/CUnpackerWrapper.cpp|x388#AEN552]]
- 4-37. [[TopLevel/SpecTcl/MySpecTclApp.cpp (comments removed)|x388#AEN556]]
- 4-38. [[TopLevel/SpecTcl/Makefile|x388#AEN560]]
- 4-39. [[TopLevel/Root/process.cpp|x388#AEN567]]
- 4-40. [[TopLevel/Root/processor.cpp (comments removed)|x388#AEN571]]
- 4-41. [[TopLevel/Root/Makefile|x388#AEN575]]

---

|  |  |  |
| --- | --- | --- |
|  |  | Next |
|  |  | Introduction and motivation. |
