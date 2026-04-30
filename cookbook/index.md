<a name="AEN1"></a># <a name="AEN2"></a>The NSCLDAQ cookbook

### <a name="AEN4"></a>Ron Fox


---

- **Table of Contents**
- 1. [Introduction](https://github.com/FRIBDAQ/docs/tree/main/cookbook/c13.md)
- 2. [Reading NSCLDAQ data sources](https://github.com/FRIBDAQ/docs/tree/main/cookbook/c35.md)
  - 2.1. [Background](https://github.com/FRIBDAQ/docs/tree/main/cookbook/c35.md#sec.readbackground)
  - 2.2. [The code](https://github.com/FRIBDAQ/docs/tree/main/cookbook/x78.md)
- 3. [Writing ring items to a data sink](https://github.com/FRIBDAQ/docs/tree/main/cookbook/c203.md)
  - 3.1. [Background](https://github.com/FRIBDAQ/docs/tree/main/cookbook/c203.md#sec.writebackground)
  - 3.2. [The code](https://github.com/FRIBDAQ/docs/tree/main/cookbook/x240.md)
- 4. [Peforming type independent processing](https://github.com/FRIBDAQ/docs/tree/main/cookbook/c287.md)
  - 4.1. [Background](https://github.com/FRIBDAQ/docs/tree/main/cookbook/c287.md#sec.process.background)
  - 4.2. [Annotated Code.](https://github.com/FRIBDAQ/docs/tree/main/cookbook/x322.md)
    - 4.2.1. [The process.cpp file](https://github.com/FRIBDAQ/docs/tree/main/cookbook/x322.md#sec.process.main)
    - 4.2.2. [The `CRingITemProcessor` class](https://github.com/FRIBDAQ/docs/tree/main/cookbook/x322.md#sec.process.class)
- 5. [Processing Event Built data](https://github.com/FRIBDAQ/docs/tree/main/cookbook/c572.md)
- 6. [Including EPICS data in event files.](https://github.com/FRIBDAQ/docs/tree/main/cookbook/c665.md)
  - 6.1. [The SBS readout program.](https://github.com/FRIBDAQ/docs/tree/main/cookbook/c665.md#sec.epicssbs)
  - 6.2. [The VMUSBReadout program.](https://github.com/FRIBDAQ/docs/tree/main/cookbook/x848.md)

- **List of Examples**
- 4-1. [`CRingItemProcessor`::`processScalerItem`](https://github.com/FRIBDAQ/docs/tree/main/cookbook/x322.md#AEN456)
- 4-2. [`CRingItemProcessor`::`processStateChangeItem`](https://github.com/FRIBDAQ/docs/tree/main/cookbook/x322.md#AEN479)
- 4-3. [`CRingItemProcessor`::`processTextItem`](https://github.com/FRIBDAQ/docs/tree/main/cookbook/x322.md#AEN506)
- 4-4. [`CRingItemProcessor`::`processEvent`](https://github.com/FRIBDAQ/docs/tree/main/cookbook/x322.md#AEN519)
- 4-5. [`CRingItemProcessor`::`processEventCount`](https://github.com/FRIBDAQ/docs/tree/main/cookbook/x322.md#AEN528)
- 4-6. [`CRingItemProcessor`::`processFormat`](https://github.com/FRIBDAQ/docs/tree/main/cookbook/x322.md#AEN536)
- 4-7. [`CRingItemProcessor`::`processGlomParams`](https://github.com/FRIBDAQ/docs/tree/main/cookbook/x322.md#AEN545)
- 4-8. [`CRingItemProcessor`::`processUnknownItemType`](https://github.com/FRIBDAQ/docs/tree/main/cookbook/x322.md#AEN565)

---
