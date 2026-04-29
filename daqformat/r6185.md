|  |  |  |
| --- | --- | --- |
| NSCLDAQ Unified Format Library |
| Prev |  | Next |


---

# <a name="AEN6185"></a>CRingScalerItem (v11)

<a name="AEN6189"></a>## Name

CRingScalerItem (v11) -- Encapsulate periodic scaler ring items.

<a name="AEN6192"></a>## Synopsis

```
#include <v11/CRingScalerItem.h>

namespace v11 {
/*!
   This class derived from CRingItem and represents a set of scalers that have been 
   formatted as a ring item.  
*/
class CRingScalerItem : public ::CRingScalerItem
{


public:
  CRingScalerItem(size_t numScalers);
  CRingScalerItem(uint32_t startTime,
		  uint32_t stopTime,
		  time_t   timestamp,
		  std::vector<uint32_t> scalers,
                  bool                  isIncremental = true,
                  uint32_t              sid = 0,
                  uint32_t              timeOffsetDivisor = 1);
  CRingScalerItem(uint64_t eventTimestamp, uint32_t source, uint32_t barrier,
                  uint32_t startTime,
		  uint32_t stopTime,
		  time_t   timestamp,
		  std::vector<uint32_t> scalers,
                  uint32_t timeDivisor = 1, bool incremental=true);
  virtual ~CRingScalerItem();

  virtual void     setStartTime(uint32_t startTime);
  virtual uint32_t getStartTime() const;
  virtual float    computeStartTime() const;
  
  virtual void     setEndTime(uint32_t endTime);
  virtual uint32_t getEndTime() const;
  virtual float    computeEndTime() const;

  virtual uint32_t getTimeDivisor() const;

  virtual void     setTimestamp(time_t stamp);
  virtual time_t   getTimestamp() const;
  
  virtual bool isIncremental() const;

  virtual void     setScaler(uint32_t channel, uint32_t value) ;
  virtual uint32_t getScaler(uint32_t channel) const ;
  virtual std::vector<uint32_t> getScalers() const;

  virtual uint32_t getScalerCount() const;
  virtual uint32_t getOriginalSourceId() const;


  virtual void* getBodyPointer();
  virtual const void* getBodyPointer() const;
  virtual bool hasBodyHeader() const;
  virtual void* getBodyHeader() const;
  
  virtual void setBodyHeader(
      uint64_t timestamp, uint32_t sourceId,
      uint32_t barrierType = 0
  );
  virtual std::string typeName() const;
  virtual std::string toString() const;

};
}
                
```

<a name="AEN6194"></a>## DESCRIPTION

Periodically NSCLDAQ readout frameworks can read a set of
                    counters or *scalers* as they are called.
                    In v11, this readout results in a ring item with the type:
                    v11::PERIODIC_SCALERS.

There are two tactics that can be employed to read scaler data.



1. Read and clear - or *incremental*
                             as it's referred to.  In that scheme scalers are
                             read and cleared so that each set of scaler values represents
                             an incremental set of counts since the last read.
2. Cummulative - or *non-incremental*
                             as the NSCLDAQ calls it.  In that scheme the scalers
                             are allowed to free run and the analysis software
                             must deal with the wrap-arounds that may occur in
                             each channel.

While the analysis of incremental scalers is simpler, there
                    are scaler devices that cannot be atomically read and clear,
                    resulting in some time skew between the readout of the
                    first channel and readout of the last channel of a module
                    that is exacerbated somewhat by the commmon clear time

Specifically incremental scaler reads will lose counts that
                    occur between the read of a channel and its subsequent clear.
                    The severity of this problem depends both on the counting
                    rates (more severe at high counting rates) of the channel and
                    the precision required of the data from that channel.

Note that read skew still occurs for cummulative readout
                    but eventually all counts are seen since the scalers are
                    never cleared.

The verison 11 scaler ring items provide a flag that
                    can specify if the scaler readout was incremental or non-incremental.

<a name="AEN6211"></a>## METHODS



`  CRingScalerItem(size_t  numScalers);`Constructs a scaler item large enough to hold
                            `numScalers` 32 bit scaler counters.
                            The start/stop time offsets are both set to
                            0 as are the scaler values.
                            The time divisor is initialized to 1
                            and the clock time is set to the time at which
                            the item was constructed.

`  CRingScalerItem(uint32_t  startTime, uint32_t  stopTime,, time_t    timestamp, std::vector<uint32_t>  scalers,, bool  isIncremental = true, uint32_t  sid = 0, uint32_t   timeOffsetDivisor = 1);`Fully constructs a scaler item.  The scaler values
                            are passed in via the `scalers`
                            parameter.  The size of that vector determines
                            the number of scalers the item will hold.

The interval start and stop offsets are given
                            by `startTime` and
                            `stopTime` respecively.
                            The optional `timeOffsetDivisor`
                            parameter provides the number of ticks in these
                            offset values per second providing support for
                            sub-second time resolution.

THe clock time is provided by
                            `timestamp`.

If `isIncremental` is false,
                            the counts are assumed to accumulate for the length
                            of the run.  Otherwise the counts in the scalers are
                            assumed to represent the counts over the interval
                            defined by `startTime`
                            through `stopTime`.

The `sid` is used to initialize
                            the source id field of the body header for this item.
                            The timestamp is initialized to a value that asks the
                            event builder to assign a timestap to the item.
                            The barrier type of the body header is set to
                            0 (no barrier).

` virtual void      setStartTime(uint32_t  startTime);`Sets the offset into the run at which the scaler counting
                            interval began.

` const virtual uint32_t  getStartTime() ();`Returns the offset into the run at which the
                            scaler counting began.  See next method, however.

` virtual float     computeStartTime();`Uses the scaler interval start offset and the
                            counting divisor to compute the start time offset
                            in seconds.

` virtual void      setEndTime(uint32_t  endTime);`Sets the offset into the run of the end of the
                            scaler counting interval

` const virtual uint32_t  getEndTime();`Returns the offset into the run at which the scaler
                            counting interval ended.  See, however the next
                            method.

` const virtual float     computeEndTime();`Using the end offset and the offset divisor computes
                            and returns the number of seconds into the run at
                            which the scaler counting interval ended.

` const virtual uint32_t  getTimeDivisor();`Returns the number of ticks in the start and end
                            time offsets that correspond to a second.

` virtual void      setTimestamp(time_t  stamp);`Sets the clock time associated with the item
                            to be `stamp`.

` const virtual time_t    getTimestamp();`Returns the clock time associated with the item.

` virtual bool  isIncremental();`If the scalers are cleared after each read, this
                            returns true, if they are allowed
                            to accumulate across counting intervals, this returns
                            false

` virtual void      setScaler(uint32_t  channel, uint32_t  value);`Sets the counts for the scaler  selected by
                            `channel` to
                            `value`. If `channel`
                            is out of range an `std::out_of_range`
                            exception is thrown.

` const virtual uint32_t  getScaler(uint32_t  channel);`Returs the value of the scaler selected by
                            `channel`.  If
                            `channel` is out of range a
                            `std::out_of_range`
                            exception is thrown.

` const virtual std::vector<uint32_t>  getScalers();`Returns a vector containing the values of the scaler
                            counts in the item.

` const virtual uint32_t  getScalerCount();`Returns the number of scalers in the item.

`  const  virtual uint32_t  getOriginalSourceId();`Returns the original source id field from the item.
                            Version 11 does not support orginal source ids and therefore
                            if there's a body header the source id from the body
                            header is returned, if not 0
                            is returned.

` const virtual void*  getBodyHeader();`Returns a pointer to the item's body header
                            or nullptr if it does not have one.

` virtual void  setBodyHeader(   uint64_t  timestamp, uint32_t  sourceId, uint32_t  barrierType = 0);`Sets new values for the body header of the item
                            if it already has one or creates a new one if it does not.

` const virtual std::string  typeName();`Returns a string that identifies the type of the item:
                            Scaler

` const virtual std::string  toString();`Returns a string that details the contents of the
                            item.  This is used by e.g. **dumper**
                            to produce a formated dump of a stream of ring items.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CRingPhysicsEventCountItem (v11) | Up | CRingStateChangeItem (v11) |
