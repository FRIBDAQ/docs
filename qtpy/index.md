[← Plotting window](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c89.md) | [Home](https://github.com/FRIBDAQ/docs/tree/main/Home.md) | [Format of Ring bufffer DAQ event files →](https://github.com/FRIBDAQ/docs/tree/main/ringtutorial/a1882.md)

---

<a name="AEN1"></a># <a name="AEN2"></a>CutiePie (QtPy) (version 5.13-000)

### <a name="AEN4"></a>Giordano Cerizza


---

- **Table of Contents**
- 1. [Introduction](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c13.md)
- 2. [A brief design description.](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c25.md)
- 3. [Features](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c28.md)
- 4. [Plotting window](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c89.md)
- 5. [Gating and summing regions](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c119.md)
- 6. [How to start CutiePie](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c162.md)
- 7. [Standalone CutiePie](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c168.md)
- 8. [Step by step tutorial](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c171.md)
- 9. [How to customize ML algo and fitting functions](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c203.md)

- **List of Figures**
- 3-1. [CutiePie GUI main window.](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c28.md#AEN31)
- 3-2. [Output popup window.](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c28.md#AEN43)
- 3-3. [Extra function popup window.](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c28.md#AEN50)
- 3-4. [Fitting popup window.](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c28.md#AEN58)
- 3-5. [Peak finder popup window.](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c28.md#AEN65)
- 3-6. [Overlay image popup window.](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c28.md#AEN72)
- 3-7. [Example of overlaid image on a plot.](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c28.md#AEN77)
- 3-8. [Example of Jupyter notebook.](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c28.md#AEN84)
- 4-1. [Canvas quick actions](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c89.md#AEN92)
- 4-2. [Copy Properties](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c89.md#AEN106)
- 5-1. [Creating a gate](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c119.md#AEN122)
- 5-2. [Editing a gate](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c119.md#AEN127)
- 5-3. [A selected contour will turn into a filled polygon](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c119.md#AEN132)
- 5-4. [By clicking once on the polygon, you can drag it anywhere you need. The polygon will follow your mouse movement without keeping the button clicked.](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c119.md#AEN137)
- 5-5. [By right-clicking the polygon will return to contour updating the gate definition with the new position.](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c119.md#AEN142)
- 5-6. [A selected contour will turn into a filled polygon with marked vertices.](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c119.md#AEN147)
- 5-7. [By clicking on a vertex and dragging it, one can modify the shape of the gate. If needed, one can add a vertex by using the key-binding i (insert)
	  or remove a vertex with d (delete)](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c119.md#AEN152)
- 5-8. [By right-clicking the polygon will return to contour updating the gate definition with the new position.](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c119.md#AEN157)

- **List of Examples**
- 6-1. [SpecTclInit.tcl](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c162.md#AEN165)
- 9-1. [ML algorithm skeleton.](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c203.md#AEN206)
- 9-2. [Example of ML algorithm based on the skeleton. The output is shown in Figure 3-5.](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c203.md#AEN209)
- 9-3. [Fitting function skeleton.](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c203.md#AEN212)
- 9-4. [Example of fitting function based on the skeleton.](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c203.md#AEN215)

---

---

[← Plotting window](https://github.com/FRIBDAQ/docs/tree/main/qtpy/c89.md) | [Home](https://github.com/FRIBDAQ/docs/tree/main/Home.md) | [Format of Ring bufffer DAQ event files →](https://github.com/FRIBDAQ/docs/tree/main/ringtutorial/a1882.md)
