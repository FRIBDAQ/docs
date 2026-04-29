|  |  |  |
| --- | --- | --- |
| SpecTcl Programming Guide. |
| Prev | Chapter 13. Capturing waveform data for display |  |


---

# <a name="AEN4507"></a>13.2. Scripting the creation of waveforms and using them

You can also script the creation of waveform objects and then use the SpecTcl API to locate
            the waveform objects you need in your event processor object.  The new **waveform**
            allows you to create and maniupulate waveform objects.  The code in the `OnAttach`
            of [[c4450#wf1.example]] is equivalent to the following Tcl,
            which can be placed in, e.g. SpecTclRC.tcl

<a name="AEN4514"></a>**Example 13-2. Scrdipting waveform objects**

```
waveform create test 100     
waveform metadata set test Frequency  100MHz bits 14 
            
```

[[x4507#wf2.create]]                    Creates the waveform named test with 100 sample points.
                [[x4507#wf2.metaset]]                    Sets the waveform metadata.

The code to locate and fill the event processor in the event processor is the same as that
            shown in [[c4450#wf1.example]].

---

|  |  |  |
| --- | --- | --- |
| Prev | Home |  |
| Capturing waveform data for display | Up |  |
