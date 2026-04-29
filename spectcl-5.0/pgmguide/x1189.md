|  |  |  |
| --- | --- | --- |
| SpecTcl Programming Guide. |
| Prev | Chapter 4. The SpecTcl API | Next |


---

# <a name="sec.api.objects"></a>4.6. The API and SpecTcl Objects.

In this section we're going to look at a few of the other SpecTcl
            objects that the SpecTcl API can return:



`getInterpreter`Returns the `CTCLInterpreter*` pointer
                        that wraps SpecTcl's main Tcl interpreter.  You can use
                        this to create new command, access variables and, in
                        general perform any operation supported by the
                        Tcl++ library and Tcl API.

`GetHistogrammer`In most cases you don't need this.  The histogrammer
                        object is a special element of the event sink pipeline.
                        It does all the gate checking and histogramming on
                        `CEvent` objects produced
                        by the event processing pipeline.

`GetAnalyzer`Returns the `CAnalyzer*` pointer to
                        the analyzer that's controlling the flow of
                        analysis.  In SpecTcl 5.0, unless replaced this is
                        a `CTclAnalyzer` object.

`GetEventSinkPipeline`Returns a `CEventSinkPipeline*`.
                        A pointer to the event sink pipeline.
                        pointer.  In general you don't need this object.
                        You can do what you need to do with the
                        event sink pipeline part of the API.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| The API and the event sink pipeline | Up | The SpecTcl event sink pipeline. |
