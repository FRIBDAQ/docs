|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN65591"></a>VX2750EventSegment

<a name="AEN65595"></a>## Name

VX2750EventSegment -- Event segment for single VX2750 DPP-PHA module

<a name="AEN65598"></a>## Synopsis

```
#include <VX2750EventSegment.h>

namespace caen_nscldaq {

class VX2750EventSegment : public ::CEventSegment
{

public:
    VX2750EventSegment(
        CExperiment *pExperiment, uint32_t sourceId,
        const char* pModuleName, VX2750TclConfig* pConfig,
        const char* pHostOrPid, bool fIsUsb = false
    );
    
    VX2750Pha* getModule() {return m_pModule;}
    

    // Event segment interface
    
    virtual void initialize();                  // at begin run.
    virtual void disable();                     // at end run.
    virtual void onPause();                     //  Just will disable.
    virtual void onResume();                    // just will initilialize.
    
    
    virtual size_t read(void* pBuffer, size_t maxwords);  // At trigger.
    
};

}               
                    
```

<a name="AEN65600"></a>## DESCRIPTION

We have seen that the `TclConfiguredReadout`
                        manages a set of modules. Techinically, it is what
                        the SBS readout framework calls a
                        *compound event segment*.
                        Compound event segments are containers for other
                        event segments. Their event segment interface methods
                        simply visit all of the event segments they contain
                        invoking the corresponding method for the contained
                        segments.

The `TclConfiguredReadout` class
                        is special purpose in that it only contains event segments
                        of type `VX2750EventSegment`.
                        These event segments are responsible for reading a single
                        nextgen CAEN digitizer running DPP-PHA firmward.

<a name="AEN65608"></a>## METHODS

Once more the event segment interface methods are omitted
                        for brevity.



`  VX2750EventSegment(CExperiment* pExperiment, uint32_t  sourceId, const char*  pModuleName, VX2750TclConfig*  pConfig, const char*  pHostOrPid, bool  fIsUsb  = false);`Constructor for an instance of the class.
                                `pExperiment` is a pointer
                                to the SBS readout framework's
                                `CExperiment` singleton instance.
                                That object controls the overall flow of acquisition
                                and provides services to other components of the framework.

`sourceId` is a unique
                                integer that will tag the event identifying the
                                source to the event builder. The source id will
                                carry through the fragment of the built event
                                all the way down the event acquisition pipeline.

`pConfig` is a Tcl drive configuration
                                object that includes the configuration of, at least
                                this module.  The configuration for this module is
                                identified by `pModuleName`
                                within the configurations held by
                                `pConfig`.  If, by the time
                                the module needs to be initialized there is no
                                configuration for `pModuleName`,
                                initialization (and hence the start of a run) will
                                terminate in failure.

`pHostOrPid` is the connection
                                paramter.  Either a host IP address or the module
                                PID depending on how it is connected to the host.
                                `fIsUsb` identifies the
                                connection type.  This parameter is optional and
                                defaults to false meaning
                                ETHERNET is used to connect the module
                                (`pHostOrPid` is an IP address),
                                if provided and true,
                                the module is connected via USB and
                                `pHostOrPid` must be the module's
                                PID.

` VX2750Pha* getModule()();`When the `VX2750EventSegment`
                                is constructed it also constructs a
                                `VX2750Pha` object which
                                is used to communicate with the physical module.
                                This object has a lifetime that is the same as
                                the lifetime of the `VX2750EventSegment`
                                that created it.  This method allows client software
                                to obtain a pointer to the module for e.g.
                                special applications.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| TclConfiguredReadout | Up | VX2750MultiTrigger |
