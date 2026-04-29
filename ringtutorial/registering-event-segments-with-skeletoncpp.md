|  |  |  |
| --- | --- | --- |
| NSCL Ring buffer DAQ tutorial |
| Prev | Chapter 3. Creating a Readout program from a spectrodaq production readout program | Next |


---

# <a name="AEN962"></a>3.3. Registering event segments with Skeleton.cpp

You must do three things in Skeleton.cpp.
                You need to select an event trigger, a dead time management
                scheme (busy) and you need to register
                your event segment(s).

In the production readout program,
                the event trigger was built in and you had to do something
                special to replace it with one that was not built in.
                As people developed other ways to trigger their readouts this
                became cumbersome.  Therefore the RingDaq readout software
                requires you to explicitly select the trigger you want to use.

The RingDaq triggers supports two trigger modules directly:
                `CCAENV262Trigger` and
                `CV977Trigger` which support triggers
                from the CAEN V262 and CAEN V977 input registers respectively.
                In addition, the device support software provides a
                class (`CCAMACTrigger`)
                that can easily be wrapped into an event trigger that supports
                the IT2 input of the CES CBD8210 CAMAC
                branch highway driver as a trigger.  The base class
                `CEventTrigger` supports the creation of
                custom event triggers.

The RingDaq readout framework also provides
                `CCAENV262Busy` and
                `CCAENV977Busy` classes  that allow those
                two modules to do dead-time management. The base class
                `CBusy` supports the creation of
                custom dead-time management schemes.

In the example we are going to give, we will:



- Set up the CAEV V262 module to handle triggers
                          and dead-time management.
- Create and register an instance of the
                          `MyEventSegment` we ported in the
                          example in the previous section of this tutorial.

<a name="AEN985"></a>**Example 3-7. Setting up triggers and registering an event segment**

```
#include <config.h>
#include <Skeleton.h>
#include <CExperiment.h>
#include <TCLInterpreter.h>
#include <CTimedTrigger.h>

#include <MyEventSegment.h>     
#include <CCAENV262Trigger.h>
#include <CCAENV262Busy.h>

...
void
Skeleton::SetupReadout(CExperiment* pExperiment)
{
  CReadoutMain::SetupReadout(pExperiment);

  // Establish your trigger here by creating a trigger object
  // and establishing it.

  pExperiment->EstablishTrigger(new CCAENV262Trigger(0x444400)); 
  pExperiment->EstablishBusy(new CCAENV262Busy(0x444400));

  // Create and add your event segments here, by creating them and invoking CExperiment's 
  // AddEventSegment

  pExperiment->AddEventSegment(new MyEventSegment(0x10000000, 0xa5)); 
}


                
```

[[x962#SDAQToRing_skelincludes]]                        The three headers below are required for our modifications
                        to the skeleton code.  We need MyEventSegment.h
                        in order to register our event segment and
                        the two CCAENV262.... headers to
                        specify the trigger and busy devices.
                    [[x962#SDAQToRing_TriggerBusy]]                        These lines are our first additions to the
                        `SetupReadout` method.
                        They create and register the appropriate objects
                        to use a CAEN V262 at base address 0x444400
                        in VME crate 0 the trigger and busy management module.
                    [[x962#SDAQToRing_evsegment]]                        Creates and registers our
                        event segment to respond to the event trigger.

To users of the production readout, this should be familiar
                territory, with the exception of the need to explicitly register
                trigger and busy management objects.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Porting existing event segments to RingDaq | Up | Porting scaler readout to RingDaq |
