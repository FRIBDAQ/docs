|  |  |  |
| --- | --- | --- |
| NSCLDAQ Unified Format Library |
| Prev |  | Next |


---

# <a name="AEN4075"></a>CRingStateChangeItem (v10)

<a name="AEN4079"></a>## Name

CRingStateChangeItem -- Encapsulate run state change ring items.

<a name="AEN4082"></a>## Synopsis

```
#include <v10/CRingStateChangeItem.h>

namespace v10 {

class CRingStateChangeItem : public ::CRingStateChangeItem
{
public:
  CRingStateChangeItem(uint16_t reason = BEGIN_RUN);
  CRingStateChangeItem(uint16_t reason,
		       uint32_t runNumber,
		       uint32_t timeOffset,
		       time_t   timestamp,
		       std::string title) ;
  
  virtual void setRunNumber(uint32_t run);
  virtual uint32_t getRunNumber() const;

  virtual void setElapsedTime(uint32_t offset);
  virtual uint32_t getElapsedTime() const;
  virtual uint32_t getTimeDivisor() const;   
  virtual float    computeElapsedTime() const;

  virtual void setTitle(std::string title);
  virtual std::string getTitle() const;

  virtual void setTimestamp(time_t stamp);
  virtual time_t getTimestamp() const;
  virtual uint32_t getOriginalSourceId() const;    

  // Virtual method overrides.

  virtual void* getBodyHeader() const;    // new
  virtual void setBodyHeader(uint64_t timestamp, uint32_t sourceId,
                         uint32_t barrierType = 0);  
  virtual std::string typeName() const;
  virtual std::string toString() const;
  

};
}

                
```

<a name="AEN4084"></a>## DESCRIPTION

The NSCLDAQ readout frameworks inform programs that
                    participate in data flow of transitions in the run state
                    by emitting run state change ring items.
                    `CRingStateChangeItem` classes
                    encapsulate these items into objects that can
                    be manipulated without knowledge of the detailed
                    data format.

<a name="AEN4088"></a>## METHODS



`  CRingStateChangeItem(uint16_t  reason  = BEGIN_RUN);`Creates a state change item for the specified state
                            change type.  The offset time is set to zero, which is
                            appropriate for a begin run, the clock time stamp is
                            set to the current time.  The run number is also set
                            to zero.  The title is set to an empty string.
                            Other version specific initialization may occur.

`   CRingStateChangeItem(uint16_t  reason, uint32_t  runNumber, uint32_t timeOffset , time_t    timestamp, std::string  title);`Full construction of a state change item.  The
                            `reason` is the type of state change
                            item as listed in DESCRIPTION.
                            `runNumber` us the number of the
                            run undergoing the transition.  `timeOffset`
                            is the offset into the run at which the transition occured.
                            This should always be 0 for
                            BEGIN_RUN transitions.

`timestamp` is the clock time
                            at which the transition occured.   This is the output
                            of the unix `time` function.

Finally, `title` is the run's title.
                            This should be the same string for all transitions
                            within a run.   Note that there is a maximum
                            length to titles defined in
                            DataFormat.h with the symble
                            TITLE_MAXSIZE. Title strings longer
                            than that should be silently truncated by the
                            version's implementation.

` virtual void  setRunNumber(uint32_t  run);`Modifies the item's run number.   This is most often
                            used when the minimal constructor is used to
                            create the item.  In that case, various methods
                            are used to fill in actual values of the fields.

` const virtual uint32_t  getRunNumber();`Return the run number from the state change ring item
                            encapsulated in the object.

` virtual void  setElapsedTime(uint32_t  offset);`Sets the raw time offset of the state change item.
                            The offset says when in the timespan of the run
                            the state change occured.  It is zero at the beginning
                            of the run.  No attempt is made to synchronize this time
                            offset between several data sources.

The units of this offset are seconds.

` const virtual uint32_t  getElapsedTime();`Returns the raw time offset stored in the event.  This
                            is the time offset in to the run at which the state change
                            occured. Note that the time divisor (see below) represents
                            the numbver of ticks in the offset in a second.

It's usually preferrable to get the offset in seconds
                            using `computeElapedTime`.

` const virtual uint32_t  getTimeDivisor();`Version 10 does not support time divisors so this
                            always returns 1

` const virtual float  computeElapsedTime();`Returns the time offset.

` virtual void  setTitle(std::string  title);`Sets the title of the run for the state transition
                            item.  The state transition items that belong to the
                            same run should have the same title.  Note that
                            there is a maximum title length and implementations
                            should silently truncate any title longer than that.

` const virtual std::string  getTitle();`Returns the value of the title string for the
                            transition object.

` virtual void  setTimestamp(time_t  stamp);`Sets a clock times associted with the item.

` const virtual time_t  getTimestamp();`Return the clock time associated with the
                            item.

` const virtual uint32_t  getOriginalSourceId();`Version 10 does not support source ids so this
                            method returns 0

` const virtual void*  getBodyHeader();`Version 10 does not support body headers, so this
                            returns a nullptr

` virtual void  setBodyHeader(uint64_t  timestamp, uint32_t  sourceId, uint32_t  barrierType  = 0);`Version 10 does not support body headers so this operation
                            does nothing.

` const virtual std::string  typeName();`Returns a string that identifies the type of the object.
                            Note that the type is a fine grained concept.
                            For examle, if the type is
                            BEGIN_RUN,
                            this method returns Begin Run.

` const virtual std::string toString();`Returns a string that describes the contents of the
                            item.  This is used by e.g.
                            **dumper** to emit formatted
                            ring items.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CRingScalerItem (v10) | Up | CRingTextItem (v10) |
