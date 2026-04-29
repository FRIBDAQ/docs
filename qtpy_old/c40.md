|  |  |  |
| --- | --- | --- |
| SpecTcl DDAS Unpackers Guide. |
| Prev |  | Next |


---

# <a name="chap.ddashit"></a>Chapter 2. The DDASHit class.

The `DAQ::DDAS::DDASHit` class provides
        information about a channel from DDAS.  DDAS events are comprised
        of hits.  Each hit provides data from a single crate/slot/channel
        of the system.  If the NSCL Event builder is used hits may be aggregated
        into events based on a coincidence window on their timestamps.

Several methods allow you to retrieve data from the hit or hits
        that comprise an event.  In addition, hit objects are copy-constructable and
        assignable.  We'll only look at the most common methods you'll need
        to know.  The remainder are described in the reference documentation.



`  const uint32_t  GetCrateID();`Returns the number of the DDAS Crate from which the hit came.
                The crate number is assigned in the cfgPixie16.txt
                file used by the Readout program that read the hit.

`  const uint32_t  GetSlotID();`Returns the slot number from which the hit was acquired.
                Slot numbers used by a readout program are described in
                cfgPixie16.txt as well.

`  const uint32_t  GetChannelID();`Returns the ID of the channel from which the hit came.  The
                hit origin is uniquely defined by the crate, slot and channel
                within the slot.

`  const double  GetTime();`Returns the calibrated timestamp of the hit.  The Readout
                software produces a timestamp based on the raw timestamp that
                has been converted to nanoseconds.  This allows the comparison
                of timestamps across modules with different clock frequencies (if
                they have been synchronized).

Note that it is an integerized version
                of this calibrated timestamp that is passed to the event builder.
                This allows events to be properly built from a system with a
                heterogeneous set of digitizers..

`  const uint32_t  GetEnergy();`Returns the energy determined by the digital pulse processing
                algorithm of the channel.

`   std::vector<uint16_t>&  GetTrace();`Returns a reference to the trace data stored for the hit.
                Note that the contents of the vector should not be considered
                well defined if the channel has been programmed not to return
                traces.

These are the most commonly used methods.  Note that the full
    documentation for this class is available in the reference section.

The remainder of this document describes frameworks that present vectors
    of hits to code that you right or, alternatively, provide configuration files
    that describe how a simplified bit of code should operate.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Introduction> |  | DDAS Data unpackers. |
