<a name="AEN1"></a># <a name="AEN2"></a>SpecTcl REST plugin

### <a name="AEN4"></a>Ron Fox


---

- **Table of Contents**
- 1. [[Introduction|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/c13.md]]
- 2. [[Incorporating the REST plugin|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/c33.md]]
- 3. [[REST requests supported.|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/c84.md]]
  - 3.1. [[General Request format|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/c84.md#AEN86]]
  - 3.2. [[Parameter requests|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x132.md]]
    - 3.2.1. [[list|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x132.md#AEN140]]
    - 3.2.2. [[edit|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x132.md#AEN181]]
    - 3.2.3. [[promote|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x132.md#AEN223]]
  - 3.3. [[spectrum requests|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x278.md]]
    - 3.3.1. [[list|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x278.md#AEN286]]
    - 3.3.2. [[delete|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x278.md#AEN323]]
    - 3.3.3. [[create|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x278.md#AEN341]]
    - 3.3.4. [[clear|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x278.md#AEN387]]
    - 3.3.5. [[contents|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x278.md#AEN395]]
  - 3.4. [[gate requests|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x449.md]]
  - 3.5. [[list|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x456.md]]
    - 3.5.1. [[Compound gates (+ * -)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x456.md#AEN479]]
    - 3.5.2. [[Slice (s)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x456.md#AEN493]]
    - 3.5.3. [[Gamma slice (gs)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x456.md#AEN508]]
    - 3.5.4. [[Simple 2-d gates (b c)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x456.md#AEN516]]
    - 3.5.5. [[Gamma bands and contours (gb gc|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x456.md#AEN534]]
    - 3.5.6. [[Bit mask gates (em am nm)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x456.md#AEN542]]
  - 3.6. [[delete|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x554.md]]
  - 3.7. [[edit|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x562.md]]
    - 3.7.1. [[Compound gates (* + -)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x562.md#AEN568]]
    - 3.7.2. [[Constant gates (T F)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x562.md#AEN573]]
    - 3.7.3. [[Bands and Contours (b c)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x562.md#AEN578]]
    - 3.7.4. [[Bit mask gates (em am nm)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x562.md#AEN587]]
    - 3.7.5. [[Slice gates (s)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x562.md#AEN595]]
    - 3.7.6. [[Gamma 2d gates (gb gc|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x562.md#AEN618]]
    - 3.7.7. [[Gamma slice (gs)|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x562.md#AEN644]]
  - 3.8. [[Gate Applications.|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x653.md]]
    - 3.8.1. [[Applying a gate to a spectrum.|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x653.md#AEN666]]
    - 3.8.2. [[Listing gate applications|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/x653.md#AEN687]]

- **List of Examples**
- 2-1. [[Incorporating and starting the REST server|https://github.com/FRIBDAQ/docs/tree/main/spectcl-5.0/restdocs/c33.md#AEN62]]

---

|  |  |  |
| --- | --- | --- |
|  |  | Next |
|  |  | Introduction |
