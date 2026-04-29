<a name="AEN1"></a># <a name="AEN2"></a>Using NSCLDAQ with a CAEN V785 Peak-Sensing ADC and CAEN V262 IO Register

### <a name="AEN4"></a>Jeromy Tompkins

### <a name="AEN7"></a>Tim Hoagland

### <a name="AEN10"></a>Ron Fox


---

**Table of Contents**1. [[PREFACE|c30]]2. [[The electronics|c51]]2.1. [[A minimal electronics setup|c51#AEN57]]3. [[Setting up the software|c116]]3.1. [[Modifying the Readout Skeleton|c116#AEN129]]3.2. [[Integrating your event segment with Readout|x216]]3.3. [[Compiling the Readout program|x228]]4. [[The dumper program|c238]]4.1. [[A very brief introduction to ring buffers|c238#AEN242]]4.2. [[Starting up the dumper program|x253]]5. [[Running the Readout Program|c282]]6. [[Interpreting the dumper output|c316]]

**List of Figures**2-1. [[A simple electronics setup for the CAEN V785|c51#AEN91]]2-2. [[Pulser Output Signal|c51#AEN97]]2-3. [[Amplifer Output Signal|c51#AEN100]]2-4. [[Amplified Signal with Logic Pulser|c51#AEN107]]2-5. [[Amplified Signal and Gate|c51#AEN111]]

**List of Examples**3-1. [[Header for MyEventSegment|c116#AEN133]]3-2. [[Impementation of CMyEventSegment|c116#AEN166]]6-1. [[The Packet Data|c316#AEN328]]

---

|  |  |  |
| --- | --- | --- |
|  |  | Next |
|  |  | PREFACE |
