|  |  |  |
| --- | --- | --- |
| Using NSCLDAQ with a CAEN V785 Peak-Sensing ADC and CAEN V262 IO Register |
| Prev | Chapter 3. Setting up the software | Next |


---

# <a name="AEN216"></a>3.2. Integrating your event segment with Readout

Once you have created one or more event segments, you must
              register them with the Readout software.  Whenever the Readout
              software must do something to its event segments, it calls the
              appropriate member function in each event segment that has been
              registered, in the order in which it has been registered.

Edit Skeleton.cpp. Towards the top of that
              file, after all the other #include statements, add:

```
#include <CCAENV262Trigger.h>
#include "MyEventSegment.h"
            
```

This is necessary because we will be creating an object of class
              MyEventSegment. We have also included a predefined class for the CCAENV262
              IO register. We use this device as a trigger interface.

Next, locate the function
              CMyExperiment::SetupReadout() Modify it to
              create an instance of MyEventSegment and
              register it to the experiment.  In this method we will also
              instantiate our trigger instance. We provide the base address as
              the argument to the CCAENV262Trigger constructor which should have
              been set using the jumper switches on the board to be 0x00100000.

```
void
CMyExperiment::SetupReadout(CExperiment* pExperiment)
{
  assert(pExperiment!=0);
  CReadoutMain::SetupReadout(pExperiment);
  pExperiment->AddEventSegment(new MyEventSegment(10, 0xff00));

  // Register a the trigger module that is situated at base address
  // 0x00100000.
  pExperiment->EstablishTrigger(new CCAENV262Trigger(0x00100000));
}
            
```

This code creates a new event segment for a CAEN V785 in slot 10,
              which will be read out into a packet with ID 0xff00.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Setting up the software | Up | Compiling the Readout program |
