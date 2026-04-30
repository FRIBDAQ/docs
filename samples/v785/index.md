<a name="AEN1"></a># <a name="AEN2"></a>Using NSCLDAQ with a CAEN V785 Peak-Sensing ADC and CAEN V262 IO Register

### <a name="AEN4"></a>Jeromy Tompkins

### <a name="AEN7"></a>Tim Hoagland

### <a name="AEN10"></a>Ron Fox


---

- **Table of Contents**
- 1. [PREFACE](https://github.com/FRIBDAQ/docs/tree/main/samples/v785/c30.md)
- 2. [The electronics](https://github.com/FRIBDAQ/docs/tree/main/samples/v785/c51.md)
  - 2.1. [A minimal electronics setup](https://github.com/FRIBDAQ/docs/tree/main/samples/v785/c51.md#AEN57)
- 3. [Setting up the software](https://github.com/FRIBDAQ/docs/tree/main/samples/v785/c116.md)
  - 3.1. [Modifying the Readout Skeleton](https://github.com/FRIBDAQ/docs/tree/main/samples/v785/c116.md#AEN129)
  - 3.2. [Integrating your event segment with Readout](https://github.com/FRIBDAQ/docs/tree/main/samples/v785/x216.md)
  - 3.3. [Compiling the Readout program](https://github.com/FRIBDAQ/docs/tree/main/samples/v785/x228.md)
- 4. [The dumper program](https://github.com/FRIBDAQ/docs/tree/main/samples/v785/c238.md)
  - 4.1. [A very brief introduction to ring buffers](https://github.com/FRIBDAQ/docs/tree/main/samples/v785/c238.md#AEN242)
  - 4.2. [Starting up the dumper program](https://github.com/FRIBDAQ/docs/tree/main/samples/v785/x253.md)
- 5. [Running the Readout Program](https://github.com/FRIBDAQ/docs/tree/main/samples/v785/c282.md)
- 6. [Interpreting the dumper output](https://github.com/FRIBDAQ/docs/tree/main/samples/v785/c316.md)

- **List of Figures**
- 2-1. [A simple electronics setup for the CAEN V785](https://github.com/FRIBDAQ/docs/tree/main/samples/v785/c51.md#AEN91)
- 2-2. [Pulser Output Signal](https://github.com/FRIBDAQ/docs/tree/main/samples/v785/c51.md#AEN97)
- 2-3. [Amplifer Output Signal](https://github.com/FRIBDAQ/docs/tree/main/samples/v785/c51.md#AEN100)
- 2-4. [Amplified Signal with Logic Pulser](https://github.com/FRIBDAQ/docs/tree/main/samples/v785/c51.md#AEN107)
- 2-5. [Amplified Signal and Gate](https://github.com/FRIBDAQ/docs/tree/main/samples/v785/c51.md#AEN111)

- **List of Examples**
- 3-1. [Header for MyEventSegment](https://github.com/FRIBDAQ/docs/tree/main/samples/v785/c116.md#AEN133)
- 3-2. [Impementation of CMyEventSegment](https://github.com/FRIBDAQ/docs/tree/main/samples/v785/c116.md#AEN166)
- 6-1. [The Packet Data](https://github.com/FRIBDAQ/docs/tree/main/samples/v785/c316.md#AEN328)

---
