|  |  |  |
| --- | --- | --- |
| NSCL Ring buffer DAQ tutorial |
| Prev | Chapter 3. Creating a Readout program from a spectrodaq production readout program | Next |


---

# <a name="AEN1003"></a>3.4. Porting scaler readout to RingDaq

Scaler readout classes area also supported by RingDaq.  This
                section describes how to port an SPDAQ Production readout scaler
                class to RingDaq and how to register it with the readout skeleton.

Let's start out with a scaler class that can read out a
                SIS 3820 scaler module for the SPDAQ production readout framework.
                The header for the starting point of our work is shown below:

<a name="AEN1007"></a>**Example 3-8. Production readout scaler class (header)**

```
#include <CScaler.h>
#include <stdint.h>


class CSIS3820;

class MyScaler : public CScaler
{
private:
  CSIS3820* m_pScaler;
public:
  MyScaler(uint32_t base, unsigned vmeCrate=0);
  virtual ~MyScaler();

  void Initialize();
  void Read(std::vector<unsigned long>& scalers);
  void Clear();
  unsigned int size();

};
                   
                
```

The implementation of this event segment is shown below.

<a name="AEN1011"></a>**Example 3-9. Production readout scaler class (implementation)**

```
#include <config.h>
#include "MyScaler.h"
#include <CSIS3820.h>

MyScaler:: MyScaler(uint32_t base, unsigned vmeCrate) :
  m_pScaler(new CSIS3820(base, vmeCrate))
{}

MyScaler:: ~MyScaler()
{
  delete m_pScaler;
}

void
MyScaler::Initialize()
{
  m_pScaler->setOperatingMode(CSIS3820::LatchingScaler);
  m_pScaler->setLatchSource(CSIS3820::LatchVMEOnly);
  m_pScaler->EnableClearOnLatch();
  m_pScaler->>nable();
  m_pScaler->Arm();
}

void
MyScaler::Clear()
{
  m_pScaler->ClearChannels();
}

unsigned int
MyScaler::size() { return 32; }

void
MyScaler:: Read(std::vector<unsigned long>& scalers)
{
  uint32_t              channels[32];

  m_pScaler->LatchAndRead(reinterpret_cast<unsigned long*>(channels));
  scalers.insert(scalers.end(), channels, channels + 32);
}
                
```

As we will see scaler classes in RingDaq are quite similar:



1. Function names are the same but begin in lower case
                           rather than upper-case (e.g. `Initialize`
                           should be changed to `initialize`).
2. The `read` method simply
                           returns an `std::vector<uint32_t>`
                           rather than appendint to one passed in.
3. There is no `size` method

A straightforward applictation of these rules leads to a header
                that looks like:

<a name="AEN1028"></a>**Example 3-10. SPDAQ Scaler to Ring Buffer (I) **

```
#include <CScaler.h>
#include <stdint.h>


class CSIS3820;

class MyScaler : public CScaler
{
private:
  CSIS3820* m_pScaler;
public:
  MyScaler(uint32_t base, unsigned vmeCrate=0);
  virtual ~MyScaler();

  void initialize();
  std::vector<uint32_t> read();
  void clear();

};
                    
                
```

Not really much to point out here.  The
                method names are all now lower case, the `size`
                method has bee removed, and the signature of the
                `read` method has been modified to
                return a vector of the data read.

The implementation really only differs in the `read`
                method and even there only trivially.  Confining ourselves to that
                code fragment from the port to the RingDaq we see:

<a name="AEN1036"></a>**Example 3-11. SPDAQ Scaler to Ring Buffer (II)**

```
...
std::vector<uint32_t>
MyScaler:: read()              
{
  uint32_t              channels[32];  
  std::vector<uint32_t> scalers; 

  m_pScaler->LatchAndRead(reinterpret_cast<unsigned long*>(channels));
  scalers.insert(scalers.end(), channels, channels + 32);
  
  return scalers;   
}
...
                
```

[[x1003#SPDAQtoRingDaq_scalerReadSignature]]                        The `read` method now returns
                        a vector rather than accepting a reference to one as a
                        parameter.
                    [[x1003#SPDAQtoRingDaq_returnVector]]                        We have declared a local vector into which the
                        data can be moved.  That vector will be returned.
                        Doing this makes the remainder of the code almost
                        identical to the previous code.
                    [[x1003#SPDAQtoRingDaq_returning]]                        Almost identical that is.  The vector we fill must be
                        returned to the caller as the function result.

Once we have ported our scalers we need to register them
                with the Skeleton.cpp.  This is done
                in  a manner that is identical to the way it is done for production
                readout code in SPDAQ:

<a name="AEN1052"></a>**Example 3-12. Registering scaler  objects with RingDaq**

```
...
#include "MyScaler.h"  
...
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

  pExperiment->AddScalerModule(new MyScaler(0x80000000)); 

}
...
                
```

[[x1003#SDPAQtoRingDaq_skeletonMyScalerHeader]]                        Includes the MyScaler.h header so that
                        the class can be instantiated into an object which
                        will be registered as a scaler.
                    [[x1003#SPDAQtoRingDaq_scalerPeriod]]                        This is the number of seconds between scaler readouts.
                    [[x1003#SPDAQtoRingDaq_skeletonAddScaler]]                        Adds the scaler to the ordered list of scalers that
                        will be read out in response to the scaler trigger.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Registering event segments withSkeleton.cpp | Up | Modifying theMakefile |
