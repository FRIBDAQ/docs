|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 11. ScalerDisplay | Next |


---

# <a name="AEN6372"></a>11.2. Why does it exist?

Scaler data, as produced by NSCLDAQ Readout programs, are passed around
      essentially as a list of 32-bit integers; each uniquely indexed by a
      channel number. In a world without the ScalerDisplay, an experimenter
      would probably use the dumper program to inspect the values of each of
      these scalers. There is absolutely nothing wrong with this method of
      inspection, in fact, doing so is typically the recommended means for
      initially debugging the proper readout of scaler modules with a Readout
      program.  However, the dumper provides no ability to label each scaler
      channel with a meaningful name and the scaler data will continually
      stream to the terminal while trying to read it. This makes its use for
      monitoring scaler data both inconvenient and arduous. The ScalerDisplay
      remedies this situation by making scaler data trivial to inspect.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| ScalerDisplay | Up | What does it do? |
