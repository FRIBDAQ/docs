[← REST requests supported.](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/c86.md) | [Home](https://github.com/FRIBDAQ/docs/tree/main/Home.md) | [Accessing the channel command (new in 5.5) →](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1042.md)

---

<a name="AEN1"></a># <a name="AEN2"></a>SpecTcl REST plugin

### <a name="AEN4"></a>Ron Fox


---

- **Table of Contents**
- 1. [Introduction](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/c15.md)
- 2. [Incorporating the REST plugin](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/c35.md)
- 3. [REST requests supported.](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/c86.md)
  - 3.1. [General Request format](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/c86.md#AEN88)
  - 3.2. [Parameter requests](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x134.md)
    - 3.2.1. [list](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x134.md#AEN142)
    - 3.2.2. [edit](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x134.md#AEN183)
    - 3.2.3. [promote](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x134.md#AEN225)
    - 3.2.4. [create](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x134.md#AEN280)
    - 3.2.5. [listnew](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x134.md#AEN310)
    - 3.2.6. [check](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x134.md#AEN316)
    - 3.2.7. [uncheck](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x134.md#AEN321)
    - 3.2.8. [version](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x134.md#AEN325)
  - 3.3. [spectrum requests](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x329.md)
    - 3.3.1. [list](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x329.md#AEN337)
    - 3.3.2. [delete](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x329.md#AEN380)
    - 3.3.3. [create](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x329.md#AEN398)
    - 3.3.4. [clear](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x329.md#AEN444)
    - 3.3.5. [contents](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x329.md#AEN452)
  - 3.4. [gate requests](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x509.md)
  - 3.5. [list](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x516.md)
    - 3.5.1. [Compound gates (+ * -)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x516.md#AEN539)
    - 3.5.2. [Slice (s)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x516.md#AEN553)
    - 3.5.3. [Gamma slice (gs)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x516.md#AEN568)
    - 3.5.4. [Simple 2-d gates (b c)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x516.md#AEN576)
    - 3.5.5. [Gamma bands and contours (gb gc](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x516.md#AEN594)
    - 3.5.6. [Bit mask gates (em am nm)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x516.md#AEN602)
  - 3.6. [delete](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x614.md)
  - 3.7. [edit](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x622.md)
    - 3.7.1. [Compound gates (* + -)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x622.md#AEN628)
    - 3.7.2. [Constant gates (T F)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x622.md#AEN633)
    - 3.7.3. [Bands and Contours (b c)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x622.md#AEN638)
    - 3.7.4. [Bit mask gates (em am nm)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x622.md#AEN647)
    - 3.7.5. [Slice gates (s)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x622.md#AEN655)
    - 3.7.6. [Gamma 2d gates (gb gc](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x622.md#AEN678)
    - 3.7.7. [Gamma slice (gs)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x622.md#AEN704)
  - 3.8. [Gate Applications.](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x713.md)
    - 3.8.1. [Applying a gate to a spectrum.](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x713.md#AEN726)
    - 3.8.2. [Listing gate applications](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x713.md#AEN747)
  - 3.9. [Attaching data sources (New in 5.5)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x779.md)
  - 3.10. [Binding Spectra to Display Memory (new in 5.5)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x851.md)
    - 3.10.1. [/sbind/all](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x851.md#AEN856)
    - 3.10.2. [/sbind/sbind](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x851.md#AEN864)
    - 3.10.3. [/sbin/list](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x851.md#AEN874)
  - 3.11. [Accessing the fit command (new in 5.5)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x903.md)
  - 3.12. [REST interface for the fold command (new in 5.5)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x992.md)
  - 3.13. [Accessing the channel command (new in 5.5)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1042.md)
  - 3.14. [Projecting spectra (new in 5.5)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1069.md)
  - 3.15. [Spectrum Underflow and Overflow Statistics (new in 5.5)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1108.md)
  - 3.16. [Access to the treeevariable command (new in 5.5)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1137.md)
  - 3.17. [Accessing the filter command (New in 5.5](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1187.md)
  - 3.18. [Accessing the integrate command (new in 5.5)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1285.md)
  - 3.19. [Accessing the SpecTcl parameter command (new in 5.4)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1337.md)
  - 3.20. [Accessing the pseudo command (new in 5.5)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1443.md)
  - 3.21. [Access to the sread command (new in 5.5)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1491.md)
  - 3.22. [Access the ringformat command (new in 5.5)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1528.md)
  - 3.23. [Accessing the unbind command (new in 5.5)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1539.md)
  - 3.24. [Accessing the ungate command (new in 5.5)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1559.md)
  - 3.25. [Accessing the swrite command (new on 5.5)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1569.md)
  - 3.26. [Controlling data anlaysis (new in 5.5)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1595.md)
  - 3.27. [Accessing the roottree command (new in 5.5)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1604.md)
  - 3.28. [Accessing the pman comman (new in 5.5)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1668.md)
  - 3.29. [Accessing the evbunpack command (new in 5.5)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1783.md)
  - 3.30. [Excuting arbitrary commands in SpecTcl (new in 5.5)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1854.md)
  - 3.31. [Traces (New in 5.5).](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1876.md)
  - 3.32. [Querying display memory mirrors.](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1945.md)
  - 3.33. [Waveform requests (new in 7.0-003)](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1973.md)
    - 3.33.1. [Creating new waveforms](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1973.md#AEN1979)
    - 3.33.2. [Listing waveform properties](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1973.md#AEN1990)
    - 3.33.3. [Retrieving waveform samples.](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1973.md#AEN2019)
    - 3.33.4. [Getting waveform metadata](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1973.md#AEN2030)
    - 3.33.5. [Modifying waveform metadata](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1973.md#AEN2047)
    - 3.33.6. [Resizing a waveform.](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1973.md#AEN2063)

- **List of Examples**
- 2-1. [Incorporating and starting the REST server](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/c35.md#AEN64)

---

---

[← REST requests supported.](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/c86.md) | [Home](https://github.com/FRIBDAQ/docs/tree/main/Home.md) | [Accessing the channel command (new in 5.5) →](https://github.com/FRIBDAQ/docs/tree/main/spectcl/restdocs/x1042.md)
