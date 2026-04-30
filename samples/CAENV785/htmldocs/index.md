[← Preface](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/f21.md) | [Home](https://github.com/FRIBDAQ/docs/tree/main/Home.md) | [Using the Readout GUI ReadoutShell →](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x1122.md)

---

<a name="AEN1"></a># <a name="AEN2"></a>Using NCSL DAQ Software to Readout a
                CAEN V785 Peak-Sensing ADC

### <a name="AEN4"></a>Timothy Hoagland

### <a name="AEN7"></a>Ron Fox


---

- **Table of Contents**
- [Preface](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/f21.md)
- 1. [The electronics](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c36.md)
  - 1.1. [A minimal Electronics Setup](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c36.md#AEN40)
- 2. [Setting up the software](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c136.md)
  - 2.1. [Readout software](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c136.md#AEN146)
    - 2.1.1. [Modifying the Readout Skeleton](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c136.md#AEN151)
    - 2.1.2. [Integrating your event segment with Readout](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c136.md#AEN286)
    - 2.1.3. [Making your Readout Executable](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c136.md#AEN298)
    - 2.1.4. [Testing the Readout Software](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c136.md#AEN307)
  - 2.2. [SpecTcl Histogramming Software](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x387.md)
    - 2.2.1. [How to copy the SpecTcl skeleton](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x387.md#AEN408)
    - 2.2.2. [How to modify the skeleton to unpack events.](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x387.md#AEN415)
    - 2.2.3. [Building the tailored SpecTcl](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x387.md#AEN735)
    - 2.2.4. [Setting up SpecTcl Spectra](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x387.md#AEN749)
- 3. [Testing and Running the Software.](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c938.md)
- 4. [More information](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c1017.md)
  - 4.1. [Scripting and desktop icons](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c1017.md#AEN1027)
    - 4.1.1. [Scripts and a desktop shortcut for SpecTcl](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c1017.md#AEN1043)
  - 4.2. [Using the Readout GUI ReadoutShell](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x1122.md)
  - 4.3. [Creating desktop icons](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x1169.md)
- 5. [Complete program listings.](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c1200.md)
  - 5.1. [Readout Software](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c1200.md#AEN1202)
  - 5.2. [SpecTcl software](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x1221.md)

- **List of Figures**
- 1-1. [A simple electronics setup for the CAEN V785](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c36.md#AEN75)
- 1-2. [Pulser Output Signal](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c36.md#AEN88)
- 1-3. [Amplifier Output SIgnal](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c36.md#AEN97)
- 1-4. [Amplified Signal with Logic pulse](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c36.md#AEN112)
- 1-5. [Amplified Signal and Gate](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c36.md#AEN123)
- 2-1. [The GUI window as it first appears.](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x387.md#AEN777)
- 2-2. [The Gui with folders open to show parameter array elements](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x387.md#AEN793)
- 2-3. [The Spectrum creation dialog box](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x387.md#AEN805)
- 2-4. [1-d Spectrum editor.](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x387.md#AEN822)
- 2-5. [Created Spectra.](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x387.md#AEN835)
- 2-6. [Initial Xamine Window](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x387.md#AEN855)
- 2-7. [The Pane Geometry dialog](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x387.md#AEN877)
- 2-8. [Spectrum Choice dialog](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x387.md#AEN895)
- 3-1. [Online source host selection dialog](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c938.md#AEN983)
- 3-2. [Sample Pulser Peak](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c938.md#AEN1007)

- **List of Examples**
- 2-1. [Header for `MyEventSegment`](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c136.md#AEN156)
- 2-2. [Implementation of `CMyEventSegment`](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c136.md#AEN223)
- 2-3. [MyEventProcessor.h - header for the event processor.](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x387.md#AEN443)
- 2-4. [Implementation of the `MyEventProcessor` class](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x387.md#AEN543)
- 4-1. [SpecTcl startup script.](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c1017.md#AEN1048)
- 4-2. [The spectcl.tcl SpecTcl
                            startup script](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c1017.md#AEN1073)
- 4-3. [Starting ReadoutShell ~/bin/startreadout](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x1122.md#AEN1148)
- 5-1. [MyEventSegment.h](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c1200.md#AEN1206)
- 5-2. [MyEventSegment.cpp](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c1200.md#AEN1209)
- 5-3. [Skeleton.cpp](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c1200.md#AEN1212)
- 5-4. [Makefile](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c1200.md#AEN1215)
- 5-5. [startreadout script](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/c1200.md#AEN1218)
- 5-6. [MyEventProcessor.h](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x1221.md#AEN1223)
- 5-7. [MyEventProcessor.cpp](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x1221.md#AEN1226)
- 5-8. [MySpecTclApp.cpp](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x1221.md#AEN1229)
- 5-9. [Makefile](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x1221.md#AEN1232)
- 5-10. [startspectcl](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x1221.md#AEN1235)
- 5-11. [SpecTcl Setup file setup.tcl](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x1221.md#AEN1238)

---

---

[← Preface](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/f21.md) | [Home](https://github.com/FRIBDAQ/docs/tree/main/Home.md) | [Using the Readout GUI ReadoutShell →](https://github.com/FRIBDAQ/docs/tree/main/samples/CAENV785/htmldocs/x1122.md)
