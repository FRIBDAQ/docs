|  |  |  |
| --- | --- | --- |
| NSCLDAQ Unified Format Library |
| Prev |  | Next |


---

# <a name="AEN1980"></a>CRingScalerItem (abstract)

<a name="AEN1984"></a>## Name

CRingScalerItem (abstract) -- Encapsulate periodic scaler readouts.

<a name="AEN1987"></a>## Synopsis

```
#include <CRingScalerItem.h>

class CRingScalerItem : public CRingItem
{
public:
  static uint32_t m_ScalerFormatMask;

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

  virtual void     setScaler(uint32_t channel, uint32_t value) ;
  virtual uint32_t getScaler(uint32_t channel) const ;
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
   


                
```

<a name="AEN1989"></a>## DESCRIPTION

Most NSCLDAQ readout frameworks have the ability to periodically
                    read a set of counters or *scalers*.
                    These counters are passed up the data flow as
                    `CRingScalerItem` objects.

In version 10, there were a pair of underlying ring item types,
                    one for incremental and a second for non-incremental, high
                    time resolution items.  In versino 11+, these were
                    combined into a single periodic scaler item.

The `CRingScalerItem` class, provides
                    interfaces that can front-end any of the underlying scaler
                    ring items.

A complication for older readouts that use CAMAC scalers are
                    devices that readout 24 bits of data but whose controllers
                    set information in the top bits.   The
                    `m_scalerFormatMask` provides a mask
                    that is bit-wise anded with scaler values before those
                    values are returned to the user.  This mask is initialized
                    by all constructors
                    to 0xffffffff, suitable for 32bit
                    scalers.  This member value is public and therefore can be
                    set to e.g.0xffffff in the event the scalers
                    are actually 24 bits wide.

<a name="AEN2001"></a>## METHODS



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

Beginning with the 12.0 data format, the
                            scaler bodies contain a field to retain the source id
                            of the data source the originally created the item.
                            This is important because event builders overwrite
                            the source id of scaler items.  This field is
                            initialized with the value of the
                            `sid` parameter.

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
| CRingPhysicsEventCountItem (abstract) | Up | CRingStateChangeItem (abstract) |
