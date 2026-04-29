<a name="AEN1"></a># <a name="AEN2"></a>The NSCLDAQ cookbook

### <a name="AEN4"></a>Ron Fox


---

- **Table of Contents**
- 1. [[Introduction|c13]]
- 2. [[Reading NSCLDAQ data sources|c35]]
  - 2.1. [[Background|c35#sec.readbackground]]
  - 2.2. [[The code|x78]]
- 3. [[Writing ring items to a data sink|c203]]
  - 3.1. [[Background|c203#sec.writebackground]]
  - 3.2. [[The code|x240]]
- 4. [[Peforming type independent processing|c287]]
  - 4.1. [[Background|c287#sec.process.background]]
  - 4.2. [[Annotated Code.|x322]]
    - 4.2.1. [[The process.cpp file|x322#sec.process.main]]
    - 4.2.2. [[The `CRingITemProcessor` class|x322#sec.process.class]]
- 5. [[Processing Event Built data|c572]]
- 6. [[Including EPICS data in event files.|c665]]
  - 6.1. [[The SBS readout program.|c665#sec.epicssbs]]
  - 6.2. [[The VMUSBReadout program.|x848]]

- **List of Examples**
- 4-1. [[`CRingItemProcessor`::`processScalerItem`|x322#AEN456]]
- 4-2. [[`CRingItemProcessor`::`processStateChangeItem`|x322#AEN479]]
- 4-3. [[`CRingItemProcessor`::`processTextItem`|x322#AEN506]]
- 4-4. [[`CRingItemProcessor`::`processEvent`|x322#AEN519]]
- 4-5. [[`CRingItemProcessor`::`processEventCount`|x322#AEN528]]
- 4-6. [[`CRingItemProcessor`::`processFormat`|x322#AEN536]]
- 4-7. [[`CRingItemProcessor`::`processGlomParams`|x322#AEN545]]
- 4-8. [[`CRingItemProcessor`::`processUnknownItemType`|x322#AEN565]]

---

|  |  |  |
| --- | --- | --- |
|  |  | Next |
|  |  | Introduction |
