|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="dataformat3-formatfunctions"></a>format  Functions

<a name="AEN23307"></a>## Name

format Functions -- Functions to create ring items.

<a name="AEN23310"></a>## Synopsis

```
#include <DataFormat.h>
           
```

<a name="AEN23312"></a>`pPhysicsEventItem formatEventitem(
              size_t nWords, 
                void* pPayload
            );`

<a name="AEN23323"></a>`pPhysicsEventCountItem formatTriggerCountItem (
                  uint32_t runTime
               , 
                time_ttimeStamp
               , 
                uint64_ttriggerCount
               );`

<a name="AEN23337"></a>`pScalerItem 
                    formatScalerItem
                (
                   unsigned  scalerCount 
                , 
                    time_ttimestamp
                , 
                    uint32_t btime
                , 
                    uint32etime
                , 
                    void* pCounters
                );`

<a name="AEN23357"></a>`pTextItem formatTextItem (
                   unsigned  nStrings 
                , 
                    time_t stamp
                , 
                    uint32_t runTime
                , 
                    const char** pStrings
                , 
                    int type
                );`

<a name="AEN23377"></a>`pStateChangeItem
                formatStateChange (
                   time_t  stamp 
                , 
                    uint32_t offset
                , 
                    uint32_t  runNumber
                , 
                    const char* pTitle
                , 
                    uin32_t type
                );`

<a name="AEN23397"></a>## DESCRIPTION

These functions produce dynamically allocated ring items
                that reflect the parameters that have been passed to them.



<a name="AEN23403"></a>`pPhysicsEventItem formatEventitem(
                          size_t nWords
                        , 
                            void* pPayload
                        );`

Creates a PHYSICS_EVENT ring item.
                            `nWords` is the number of
                            uint16_t objects that are in the event
                            data pointed to by `pPayload`.
                            When the ring item is created, a uint32_t
                            containing nWords + 2 is inserted
                            prior to the payload to conform to NSCL standards
                            for the payload contents.

<a name="AEN23424"></a>`pPhysicsEventCountItem formatTriggerCountItem (
                              uint32_t runTime
                           , 
                            time_ttimeStamp
                           , 
                            uint64_ttriggerCount
                           );`

Creates a PHYSICS_EVENT_COUNT ring
                            item.  `runTime` should be the
                            number of seconds into the run the items is emitted.
                            `timeStamp` should be the unix
                            `time(2)` at which the event
                            count is being submittted and `triggerCount`
                            is the total number of event triggers that have been
                            created by this point in the run.

<a name="AEN23447"></a>`pScalerItem 
                                formatScalerItem
                            (
                               unsigned  scalerCount 
                            , 
                                time_ttimestamp
                            , 
                                uint32_t btime
                            , 
                                uint32etime
                            , 
                                void* pCounters
                            );`

Creates a scaler ring item (INCREMENTAL_SCALERS).
                            `scalerCount` is the number of
                            scalers read out and `pCounters`
                            points to an array of uint32_t scalers.
                            `btime` and `etime`
                            are respectively the beginning and end run offsets
                            over which the scalers counted.

`timestamp` is the time at which the
                            scaler data was read.

<a name="AEN23479"></a>`pTextItem formatTextItem (
                           unsigned  nStrings 
                        , 
                            time_t stamp
                        , 
                            uint32_t runTime
                        , 
                            const char** pStrings
                        , 
                            int type
                        );`

Creates a text ring item.  The type of the
                            ring items is provided by the `type`
                            argument however this should be one of
                            PACKET_TYPES or
                            MONITORED_VARIABLES
                            or a user type that is larger than
                            FIRST_USER_ITEM_CODE.

The number of strings put in the item are
                            `nStrings` and
                            `pStrings` is a pointer to an
                            array of pointers to the null terminated strings that
                            are put in the `s_strings` storage
                            of the ring item.

`stamp` is the unix
                            `time(2)` at which the
                            item was created and `runTime`
                            the number of seconds into the run at which this time
                            was created.

<a name="AEN23515"></a>`pStateChangeItem
                        formatStateChange (
                           time_t  stamp 
                        , 
                            uint32_t offset
                        , 
                            uint32_t  runNumber
                        , 
                            const char* pTitle
                        , 
                            uin32_t type
                        );`

Formats and returns a state change item.
                            State change items reflect a change in the run state.
                            While the `type` parameter
                            provides the item type, this should normally be one of
                            BEGIN_RUN,
                            END_RUN,
                            PAUSE_RUN or
                            RESUME_RUN.

`runNumber` should be a
                            unique run number for the run and
                            `pTitle` should point to a
                            null terminated title string.

`offset` is the time into the
                            run at which the state change took place in seconds.
                            This will be 0 for
                            BEGIN_RUN and the number of
                            seconds the run was active for
                            END_RUN

Finally `stamp` is the unix
                            absolute timestamp from `time(2)`
                            at which the state change occured.

<a name="AEN23553"></a>## RETURNS

Pointers to dynamically allocated storage which has been
                filled in with the requested ring item.
                When the caller is done with the item it should pass it to 
                `free(3)` to release the storage.

If storage could not be allocated for the ring  item
                NULL is returned instead.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| DataFormat.h | Up | CDataSource |
