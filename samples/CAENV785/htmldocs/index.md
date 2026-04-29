<a name="AEN1"></a># <a name="AEN2"></a>Using NCSL DAQ Software to Readout a
                CAEN V785 Peak-Sensing ADC

### <a name="AEN4"></a>Timothy Hoagland

### <a name="AEN7"></a>Ron Fox


---

**Table of Contents**[[Preface|f21]]1. [[The electronics|c36]]1.1. [[A minimal Electronics Setup|c36#AEN40]]2. [[Setting up the software|c136]]2.1. [[Readout software|c136#AEN146]]2.1.1. [[Modifying the Readout Skeleton|c136#AEN151]]2.1.2. [[Integrating your event segment with Readout|c136#AEN286]]2.1.3. [[Making your Readout Executable|c136#AEN298]]2.1.4. [[Testing the Readout Software|c136#AEN307]]2.2. [[SpecTcl Histogramming Software|x387]]2.2.1. [[How to copy the SpecTcl skeleton|x387#AEN408]]2.2.2. [[How to modify the skeleton to unpack events.|x387#AEN415]]2.2.3. [[Building the tailored SpecTcl|x387#AEN735]]2.2.4. [[Setting up SpecTcl Spectra|x387#AEN749]]3. [[Testing and Running the Software.|c938]]4. [[More information|c1017]]4.1. [[Scripting and desktop icons|c1017#AEN1027]]4.1.1. [[Scripts and a desktop shortcut for SpecTcl|c1017#AEN1043]]4.2. [[Using the Readout GUI ReadoutShell|x1122]]4.3. [[Creating desktop icons|x1169]]5. [[Complete program listings.|c1200]]5.1. [[Readout Software|c1200#AEN1202]]5.2. [[SpecTcl software|x1221]]

**List of Figures**1-1. [[A simple electronics setup for the CAEN V785|c36#AEN75]]1-2. [[Pulser Output Signal|c36#AEN88]]1-3. [[Amplifier Output SIgnal|c36#AEN97]]1-4. [[Amplified Signal with Logic pulse|c36#AEN112]]1-5. [[Amplified Signal and Gate|c36#AEN123]]2-1. [[The GUI window as it first appears.|x387#AEN777]]2-2. [[The Gui with folders open to show parameter array elements|x387#AEN793]]2-3. [[The Spectrum creation dialog box|x387#AEN805]]2-4. [[1-d Spectrum editor.|x387#AEN822]]2-5. [[Created Spectra.|x387#AEN835]]2-6. [[Initial Xamine Window|x387#AEN855]]2-7. [[The Pane Geometry dialog|x387#AEN877]]2-8. [[Spectrum Choice dialog|x387#AEN895]]3-1. [[Online source host selection dialog|c938#AEN983]]3-2. [[Sample Pulser Peak|c938#AEN1007]]

**List of Examples**2-1. [[Header for `MyEventSegment`|c136#AEN156]]2-2. [[Implementation of `CMyEventSegment`|c136#AEN223]]2-3. [[MyEventProcessor.h - header for the event processor.|x387#AEN443]]2-4. [[Implementation of the `MyEventProcessor` class|x387#AEN543]]4-1. [[SpecTcl startup script.|c1017#AEN1048]]4-2. [[The spectcl.tcl SpecTcl
                            startup script|c1017#AEN1073]]4-3. [[Starting ReadoutShell ~/bin/startreadout|x1122#AEN1148]]5-1. [[MyEventSegment.h|c1200#AEN1206]]5-2. [[MyEventSegment.cpp|c1200#AEN1209]]5-3. [[Skeleton.cpp|c1200#AEN1212]]5-4. [[Makefile|c1200#AEN1215]]5-5. [[startreadout script|c1200#AEN1218]]5-6. [[MyEventProcessor.h|x1221#AEN1223]]5-7. [[MyEventProcessor.cpp|x1221#AEN1226]]5-8. [[MySpecTclApp.cpp|x1221#AEN1229]]5-9. [[Makefile|x1221#AEN1232]]5-10. [[startspectcl|x1221#AEN1235]]5-11. [[SpecTcl Setup file setup.tcl|x1221#AEN1238]]

---

|  |  |  |
| --- | --- | --- |
|  |  | Next |
|  |  | Preface |
