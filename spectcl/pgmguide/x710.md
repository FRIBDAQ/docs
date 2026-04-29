|  |  |  |
| --- | --- | --- |
| SpecTcl Programming Guide. |
| Prev | Chapter 3. The SpecTcl event processing pipeline. | Next |


---

# <a name="AEN710"></a>3.3. Playing back filter data

A SpecTcl filter is a mechanism that allows you to transform a raw
            data set into a decoded subset of the data.  By decoded subset we mean
            that:



- Only events that satisfy the filter's gate are written to the
                      filtered data set.
- A subset of the parameters decoded from each event are
                      written to the data set.
- The structure of the raw event is lost.

Since the structure of the raw event is lost, and since any parameter
            can be written to the output file, the event processing pipeline
            used to analyze data from a raw event file is not useful in analyzing
            filter files:



- There is no raw event to decode into raw parameters.
- Parameters computed by later stages of the pipeline can
                      already be present in the event file.

When analyzing filter files you must therefore:



- Register an initial stage of the event analysis pipeline
                      that can read the filter file.
- Register subsequent stages that compute parameters that
                      are not already present in the filter file.  You could think
                      of analysis as performing an initial broad cut on the data
                      and then subsequently only producing physically meaningful
                      parameter on this subset.  The event processor that computes
                      these parameters would be in the pipeline for analyzing
                      filtered data.

In this section, we're going to look at how to set up the first
            element of an analysis pipeline that can analyze filter data.  In
            the next section, we'll look at an extension to SpecTcl that allows
            you to dynamically switch SpecTcl between the analysis of raw data
            and filtered data.

SpecTcl provides an event processor that can decode any filter file.
            The parameters in the filter file are decoded into parameters of
            the name they had when they were written..
            If a parameter is found in the filter file, but
            is not defined in SpecTcl when the filter is read back, it is
            ignored without reporting an error.

The filter event processor element must be registered as the first
            element of the SpecTcl event processing pipeline.  To use it we must:



- #include the filter file decoder
                      event processor into MySpecTclApp.cpp.
                      This header is named FilterEventProcessor.h
                      and defines the class
                      `CFilterEventProcessor`.
- Replace the event processing pipeline definition
                      in `CreateAnalysisPipeline`
                      so that it contains an instance of
                      a `CFilterEventProcessor` class.

Note that it does no harm to leave our raw event processors linked
            in with SpecTcl. Towards the top of MySpecTclApp.cpp:

<a name="AEN748"></a>```
//////////////
#include <config.h>
#include "MySpecTclApp.h"
#include "EventProcessor.h"
#include "TCLAnalyzer.h"
#include <Event.h>
#include <TreeParameter.h>
#include "MyEventProcessor.h"                // <- this line can stay in
#include <FilterEventProcessor.h>       // <- add this line
            
```

Make `CreateAnalysisPipeline` look like
            this:

<a name="AEN752"></a>**Example 3-12. 
                Event analysis pipeline for filters.
            **

```
void
CMySpecTclApp::CreateAnalysisPipeline(CAnalyzer& rAnalyzer)
{
  RegisterEventProcessor(*(new CFilterEventProcessor), "Filter-unpacker");


}
                
            
```

Recompiling this SpecTcl (via **make**) will
                result in a SpecTcl instance that can analyze filter files.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Setting up an event analysis pipeline (the simple version) | Up | "Using the callout analysis framework |
