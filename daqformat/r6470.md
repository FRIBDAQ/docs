|  |  |  |
| --- | --- | --- |
| NSCLDAQ Unified Format Library |
| Prev |  | Next |


---

# <a name="AEN6470"></a>CRingStateChangeItem (v11)

<a name="AEN6474"></a>## Name

CRingStateChangeItem (v11) -- Encapsulate state change ring items.

<a name="AEN6477"></a>## Synopsis

```
#include <v11/CRingStateChangeItem.h>

namespace v11 {
class CRingStateChangeItem : public ::CRingStateChangeItem
{
public:
  CRingStateChangeItem(uint16_t reason = BEGIN_RUN);
  CRingStateChangeItem(uint16_t reason,
		       uint32_t runNumber,
		       uint32_t timeOffset,
		       time_t   timestamp,
		       std::string title) ;
  CRingStateChangeItem(uint64_t eventTimestamp, uint32_t sourceId, uint32_t barrierType,
                       uint16_t reason,
		       uint32_t runNumber,
		       uint32_t timeOffset,
		       time_t   timestamp,
		       std::string title,
                       uint32_t offsetDivisor = 1);

  virtual void setRunNumber(uint32_t run);
  virtual uint32_t getRunNumber() const;

  virtual void setElapsedTime(uint32_t offset);
  virtual uint32_t getElapsedTime() const;
  virtual float    computeElapsedTime() const;

  virtual void setTitle(std::string title) ;
  virtual std::string getTitle() const;

  virtual void setTimestamp(time_t stamp);
  virtual time_t getTimestamp() const;
  
  virtual uint32_t getOriginalSourceId() const;
  virtual const void*  getBodyPointer() const;
  virtual void*        getBodyPointer();
  virtual bool hasBodyHeader() const;
  virtual void* getBodyHeader() const;
  virtual void setBodyHeader(uint64_t timestamp, uint32_t sourceId,
                         uint32_t barrierType = 0);
  virtual std::string typeName() const;
  virtual std::string toString() const;

};
}

                
```

<a name="AEN6479"></a>## DESCRIPTION

When a run begins, pauses, resumes or ends (normally), the
                    NSCLDAQ readout frameworks produce state change ring items
                    to document the times at which these state changes occured.
                    `v11::CRingStateChangeItem` is intended
                    to encapsulate these ring items for version 11.

Several types of state change items are supported:
                    v11::BEGIN_RUN,
                    v11::PAUSE_RUN, v11::RESUME_RUN
                    and v11::END_RUN.  Note that not all readers
                    support pausing a run and the paused state will likely be
                    deprecated and eventually phased out.

<a name="AEN6488"></a>## METHODS



`  CRingStateChangeItem(uint16_t  reason  = BEGIN_RUN);`Creates a state change item for the specified state
                            change type.  The offset time is set to zero, which is
                            appropriate for a begin run, the clock time stamp is
                            set to the current time.  The run number is also set
                            to zero.  The title is set to an empty string.
                            Other version specific initialization may occur.

v11 supports body headers but
                            this constructor will create an item without a body
                            header.

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

` const virtual uint32_t  getElapsedTime();`Returns the raw time offset stored in the event.  This
                            is the time offset in to the run at which the state change
                            occured. Note that the time divisor (see below) represents
                            the numbver of ticks in the offset in a second.

It's usually preferrable to get the offset in seconds
                            using `computeElapedTime`.

` const virtual uint32_t  getTimeDivisor();`Returns the time divisor.  This value represents the
                            number of ticks of time offset in a second.
                            Note that at present, all constructors initialize
                            this to 1 and there is no mechanism
                            to modify the divisor.  Later releases may provide
                            such a mechanism.

` const virtual float  computeElapsedTime();`Computes the time offset stored in the item in
                            seconds.  This is the preferred method to get the
                            time offset in the presence of the capability
                            for divisors that are greater than 1.

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

` const virtual uint32_t  getOriginalSourceId();`Returns the original source id of the item.
                            Since v11 does not support original source ids,
                            if the item has a body header the source id in the
                            body header is returned, otherwise
                            0 is returned.

` const virtual void*  getBodyHeader();`Returns a pointer to the object's body header.
                            If the object has no body header
                            nullptr is returned.  The
                            actual format of the body header
                            is described in
                            v11/DataFormat.h
                            by the v11::BodyHeader
                            data type.

` virtual void  setBodyHeader(uint64_t  timestamp, uint32_t  sourceId, uint32_t  barrierType  = 0);`Adds, if no body header exists, or modifies an
                            existing body header in the object.  If the version
                            does not support body headers, the method should do
                            nothing.

Note that any body pointer or body cursor is invalidated
                            by this call if there is not already a body header to
                            modify.

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
| CRingScalerItem (v11) | Up | CRingTextItem (v11) |
