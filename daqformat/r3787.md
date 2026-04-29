|  |  |  |
| --- | --- | --- |
| NSCLDAQ Unified Format Library |
| Prev |  | Next |


---

# <a name="AEN3787"></a>CRingScalerItem (v10)

<a name="AEN3791"></a>## Name

CRingScalerItem -- Encapsulate a scaler counts ring item.

<a name="AEN3794"></a>## Synopsis

```
#include <v10/CRingScalerItem.h>

namespace v10 {
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
  
  virtual void     setScaler(uint32_t channel, uint32_t value);
  virtual uint32_t getScaler(uint32_t channel) const;
  virtual std::vector<uint32_t> getScalers() const;

  virtual uint32_t getScalerCount() const;
  virtual uint32_t getOriginalSourceId() const;


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

<a name="AEN3796"></a>## DESCRIPTION

This encapsulates a scaler ring item.  Scaler ring items contain
                    periodically read scalers.   In V10, there are two types of
                    underlying scaler ring items that, in V11 are coalesced into
                    a single type.

Scaler items of type v10::INCREMENTAL_SCALERS
                    are scalers that have a run offset resolution of one second
                    and are cleared as they are read.  Thus each scaler counter
                    represents the new counts since the last read.

v10::>
                    In the original S800 readout system, it was necessary
                    to introduce a second type: v10::TIMESTAMPED_NONINCR_SCALERS.
                    These scalers are read cumulatively and therefore analysis software
                    must be prepared to handle rollovers.  In addition,
                    subsecond time resolution was possible and therefore,
                    these items have a time offset divisor.

The constructors of `v10::CRingScalerItem`
                    use the `isIncremental`  flag in the
                    full constructor to determine which underlying item type
                    is desired.  Simple constructors always construct a
                    v10::INCREMENTAL_SCALERS item.

<a name="AEN3808"></a>## METHODS



`  CRingScalerItem(size_t  numScalers);`Constructs a scaler item large enough to hold
                            `numScalers` 32 bit scaler counters.
                            The start/stop time offsets are both set to
                            0 as are the scaler values.
                            This constructor unconditionally  produces a
                            v10::INCREMENTAL_SCALERS which
                            has no time offset divisor.

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
                            sub-second time resolution.  This is only used
                            if the scalers are non-incremental.  If scalers
                            are incremental, the time offsets must always be
                            in seconds.

THe clock time is provided by
                            `timestamp`.

If `isIncremental` is false,
                            the counts are assumed to accumulate for the length
                            of the run.  Otherwise the counts in the scalers are
                            assumed to represent the counts over the interval
                            defined by `startTime`
                            through `stopTime`.
                            This parameter determines the scaler item type.
                            If true, a
                            v10::INCREMENTAL_SCALERS
                            item is created.
                            If false, a
                            v10::TIMESTAMPED_NONINCR_SCALERS
                            item is created.

The
                            `sid` parameter is ignored
                            as source ids only were not yet introduced in any
                            of the v10 ring items.

` virtual void      setStartTime(uint32_t  startTime);`Sets the offset into the run at which the scaler counting
                            interval began.

` const virtual uint32_t  getStartTime() ();`Returns the offset into the run at which the
                            scaler counting began.  See next method, however.

` virtual float     computeStartTime();`Uses the scaler interval start offset and the
                            counting divisor to compute the start time offset
                            in seconds.  Note that for
                            v10::INCREMENTAL_SCALERS
                            items the divisor is always treated as
                            1.

` virtual void      setEndTime(uint32_t  endTime);`Sets the offset into the run of the end of the
                            scaler counting interval

` const virtual uint32_t  getEndTime();`Returns the offset into the run at which the scaler
                            counting interval ended.  See, however the next
                            method.

` const virtual float     computeEndTime();`Using the end offset and the offset divisor computes
                            and returns the number of seconds into the run at
                            which the scaler counting interval ended.
                            Note that for v10::INCREMENTAL_SCALERS
                            the divisor is always treated as 1

` const virtual uint32_t  getTimeDivisor();`Returns the number of ticks in the start and end
                            time offsets that correspond to a second.
                            For v10::INCREMENTAL_SCALERS
                            items, this is always 1.

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

` const virtual void*  getBodyHeader();`Returns  nullptr since the
                            v10 ring items don't have body headers.

` virtual void  setBodyHeader(   uint64_t  timestamp, uint32_t  sourceId, uint32_t  barrierType = 0);`Does nothing as the v10 ring items don't have body
                            headers.

` const virtual std::string  typeName();`Returns a string that identifies the type of the item:
                            Scaler

` const virtual std::string  toString();`Returns a string that details the contents of the
                            item.  This is used by e.g. **dumper**
                            to produce a formated dump of a stream of ring items.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CRingPhysicsEventCountItem (v10) | Up | CRingStateChangeItem (v10) |
