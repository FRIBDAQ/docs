|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 14. Simple V775 readout | Next |


---

# <a name="AEN8502"></a>14.7. The full readout program.

In this section we will include the full text of
            the following files:



MakefileThe Readout Makefile.

Skeleton.cppThe modified skeleton file.

V775EventSegment.hThe header for our event segment class.

V775EventSegment.cppThe implementation of our event segment.

MyTrigger.hThe header for our trigger class.

Mytrigger.cppThe implementation of our trigger class.

<a name="AEN8536"></a>**Example 14-19. Makefile**

```
#
#  This establishes which version of NSCLDAQ we're using and where it's installed:
#  Supposedly  you only need to change this definition to update to a newer
#  version of the software:

INSTDIR=/usr/opt/daq/11.0-rc18

include $(INSTDIR)/etc/SBSRdoMakeIncludes



USERCCFLAGS=
USERCXXFLAGS=$(USERCCFLAGS)

USERLDFLAGS=

OBJECTS=Skeleton.o V775EventSegment.o MyTrigger.o

Readout: $(OBJECTS)
        $(CXXLD) -o Readout $(OBJECTS) $(USERLDFLAGS) $(LDFLAGS)

clean:
        rm -f $(OBJECTS) Readout

depend:
        makedepend $(USERCXXFLAGS) *.cpp *.c


help:
        echo make           - Build Readout.
        echo make clean     - Remove products from previous builds.
        echo make depend    - Add header dependencies to Makefile.

            
```

<a name="AEN8540"></a>**Example 14-20. Skeleton.cpp**

```
#include <config.h>
#include <Skeleton.h>
#include <CExperiment.h>
#include <TCLInterpreter.h>
#include <CTimedTrigger.h>

#include <CAENcard.h>
#include "V775EventSegment.h"
#include "MyTrigger.h"

CTCLApplication* gpTCLApplication = new Skeleton;

static const uint32_t V775Base=0x11110000;  // Base address of the V775.

void
Skeleton::SetupReadout(CExperiment* pExperiment)
{
  CReadoutMain::SetupReadout(pExperiment);

  CAENcard* pModule = new CAENcard(10, 0, false, V775Base);


  // Establish your trigger here by creating a trigger object
  // and establishing it.

  pExperiment->EstablishTrigger(new MyTrigger(*pModule));


  // Create and add your event segments here, by creating them and invoking CExperiment's
  // AddEventSegment

  pExperiment->AddEventSegment(new CV775EventSegment(*pModule));


}
void
Skeleton::SetupScalers(CExperiment* pExperiment)
{
  CReadoutMain::SetupScalers(pExperiment);      // Establishes the default scaler trigger.

  // Sample: Set up a timed trigger at 2 second intervals.

  timespec t;
  t.tv_sec  = 2;
  t.tv_nsec = 0;
  CTimedTrigger* pTrigger = new CTimedTrigger(t);
  pExperiment->setScalerTrigger(pTrigger);

  // Create and add your scaler modules here.


}

void
Skeleton::addCommands(CTCLInterpreter* pInterp)
{
  CReadoutMain::addCommands(pInterp); // Add standard commands.
}


void
Skeleton::SetupRunVariables(CTCLInterpreter* pInterp)
{
  // Base class will create the standard commands like begin,end,pause,resume
  // runvar/statevar.

  CReadoutMain::SetupRunVariables(pInterp);

  // Add any run variable definitions below.

}

void
Skeleton::SetupStateVariables(CTCLInterpreter* pInterp)
{
  CReadoutMain::SetupStateVariables(pInterp);

  // Add any state variable definitions below:


}
            
            
```

<a name="AEN8544"></a>**Example 14-21. V775EventSegment.h**

```
#ifndef _V775EVENTSEGMENT_H
#define _V775EVENTSEGMENT_H

#include <CEventSegment.h>

class CAENcard;



class CV775EventSegment : public CEventSegment
{
private:
  CAENcard&   m_module;

public:
  CV775EventSegment(CAENcard& module);

public:
  virtual void initialize();

  virtual size_t read(void* pBuffer, size_t maxwords);
};
                
            
```

<a name="AEN8548"></a>**Example 14-22. V775EventSegment.cpp**

```
#include "V775EventSegment.h"
#include <CAENcard.h>
#include <iostream>
#include <stdint.h>


static const unsigned TDC_RANGE = 0x1e;         // Corresponds to 1.2usec.
static const unsigned  MAX_WORDS = 34*sizeof(uint32_t)/sizeof(uint16_t);



CV775EventSegment::CV775EventSegment(CAENcard& module) :
  m_module(module)
{}

void
CV775EventSegment::initialize()
{
  try {
    m_module.commonStart();
    m_module.setRange(TDC_RANGE);
    m_module.clearData();
  }
  catch (std::string msg) {
    std::cerr << "Unable to initialize TDC (V775)\n";
    std::cerr << msg << std::endl;
    throw;
  }
}

size_t
CV775EventSegment::read(void* pBuffer, size_t maxWords)
{
  if (MAX_WORDS <= maxWords) {
    size_t n =  m_module.readEvent(pBuffer);
    m_module.clearData();
    return n/sizeof(uint16_t);
  } else {
    throw std::string("CV775EventSegment::read - maxWords won't hold my worst case event");
  }
}
                
            
```

<a name="AEN8552"></a>**Example 14-23. MyTrigger.h**

```
#ifndef _MYTRIGGER_H
#define _MYTRIGGER_H

#include <CEventTrigger.h>

class CAENcard;

class MyTrigger : public CEventTrigger
{
private:
  CAENcard& m_module;
public:
  MyTrigger(CAENcard& module);

  virtual bool operator()();
};
                
            
```

<a name="AEN8555"></a>**Example 14-24. MyTrigger.cpp**

```

#include "MyTrigger.h"
#include <CAENcard.h>


MyTrigger::MyTrigger(CAENcard& module) :
  m_module(module)
{}

bool
MyTrigger::operator()() {
  return m_module.dataPresent();
}
            
```

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Taking the example further. | Up | The full SpecTcl program. |
