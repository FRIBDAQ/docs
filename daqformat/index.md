<a name="AEN1"></a># <a name="AEN2"></a>NSCLDAQ Unified Format Library

### <a name="AEN4"></a>Ron Fox


---

- **Table of Contents**
- 1. [[Introduction|https://github.com/FRIBDAQ/docs/tree/main/daqformat/c13.md]]
  - 1.1. [[Motivation|https://github.com/FRIBDAQ/docs/tree/main/daqformat/c13.md#AEN15]]
  - 1.2. [[Document Organization|https://github.com/FRIBDAQ/docs/tree/main/daqformat/x20.md]]
    - 1.2.1. [[Incorporating this library into your programs|https://github.com/FRIBDAQ/docs/tree/main/daqformat/x20.md#AEN35]]
- 2. [[Library Organization|https://github.com/FRIBDAQ/docs/tree/main/daqformat/c49.md]]
  - 2.1. [[Ring Item classes.|https://github.com/FRIBDAQ/docs/tree/main/daqformat/c49.md#sec.ringitems]]
  - 2.2. [[Factories.|https://github.com/FRIBDAQ/docs/tree/main/daqformat/x115.md]]
- 3. [[Factories and the Abstract Factory Pattern|https://github.com/FRIBDAQ/docs/tree/main/daqformat/c171.md]]
- 4. [[Reference pages|https://github.com/FRIBDAQ/docs/tree/main/daqformat/c263.md]]
  - 4.1. [[Abstract Formatting|https://github.com/FRIBDAQ/docs/tree/main/daqformat/c263.md#AEN267]]
    - [[Format Selector|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r269.md]] -- Select Specific Format Factory
    - [[RingItemFactoryBase|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r324.md]] -- Provide interface for ring item factoires.
    - [[CRingItem (abstract)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r974.md]] -- Ultimate ring item base class
    - [[CAbnormalEndItem (abstract)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r1256.md]] -- Support ring items that flag abnormally ended runs.
    - [[CDataFormatItem (abstract)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r1332.md]] -- Ring item that describes format version
    - [[CGlomParameters (abstract)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r1418.md]] -- Document event building parameters
    - [[CPhysicsEventItem (abstract)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r1551.md]] -- Encapsulate the data from a physics trigger.
    - [[CRingFragmentItem (abstract)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r1633.md]] -- Ring item to encapsulate event builder fragments.
    - [[CRingPhysicsEventCountItem (abstract)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r1782.md]] -- Ring Item with trigger counts.
    - [[CRingScalerItem (abstract)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r1980.md]] -- Encapsulate periodic scaler readouts.
    - [[CRingStateChangeItem (abstract)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r2258.md]] -- Encapsulate run state change items.
    - [[CRingTextItem (abstract)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r2481.md]] -- Encapsulate a ring item of text strings
    - [[CUnknownFragment (abstract)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r2688.md]] --
  - 4.2. [[NSCLDAQ version 10 format|https://github.com/FRIBDAQ/docs/tree/main/daqformat/x2702.md]]
    - [[RingItemFactory (version 10)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r2708.md]] -- Generate v10 ring item objects.
    - [[CRingItem (version 10)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r3350.md]] -- Version 10 ring item class.
    - [[CRingFragmentItem (version 10)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r3462.md]] -- Event builder fragment
    - [[CRingPhysicsEventCountItem (v10)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r3609.md]] -- Encapsulate trigger count ring item.
    - [[CRingScalerItem (v10)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r3787.md]] -- Encapsulate a scaler counts ring item.
    - [[CRingStateChangeItem (v10)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r4075.md]] -- Encapsulate run state change ring items.
    - [[CRingTextItem (v10)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r4291.md]] -- Encapsulate a set of textual strings
  - 4.3. [[NSCLDAQ version 11 format|https://github.com/FRIBDAQ/docs/tree/main/daqformat/x4479.md]]
    - [[RingItemFactory (v11)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r4523.md]] -- Create ring items in version 11 format.
    - [[CRingItem (v11)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r5155.md]] -- Encapsulate version 11 ring items.
    - [[CAbnormalEndItem (v11)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r5443.md]] -- Encapsulate abnormal end run item.
    - [[CDataFormatItem (v11)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r5516.md]] -- Provide the format version of subsequent data
    - [[CGlomParameters (V11)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r5603.md]] -- Document event builder parameters.
    - [[CPhysicsEventItem (v11)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r5748.md]] -- Encapsulate a physics event.
    - [[CRingFragmentItem (v11)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r5828.md]] -- Encapsulate an event builder fragment.
    - [[CRingPhysicsEventCountItem (v11)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r5983.md]] -- Encapsulate trigger count ring item.
    - [[CRingScalerItem (v11)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r6185.md]] -- Encapsulate periodic scaler ring items.
    - [[CRingStateChangeItem (v11)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r6470.md]] -- Encapsulate state change ring items.
    - [[CRingTextItem (v11)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r6694.md]] -- Encapsulate text strings.
    - [[CUnknownFragment (v11)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r6896.md]] -- Event buider fragments with non ringitem payloads.
  - 4.4. [[NSCLDAQ Version 12 format|https://github.com/FRIBDAQ/docs/tree/main/daqformat/x6910.md]]
    - [[RingItemFactory (v12)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r6920.md]] -- Create ring items formatted for version 12.
    - [[CRingItem (v12)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r7555.md]] -- Encapsulate V12 undifferentiated ring item
    - [[CAbnormalEndItem (v12)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r7855.md]] -- Encapsulate abnormal end run item.
    - [[CDataFormatItem (v12)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r7928.md]] -- Document the version of NSCLDAQ format that follows
    - [[CGLomParameters (v12)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r8016.md]] -- Document event builder parameters.
    - [[CPhysicsEventItem  (v12)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r8164.md]] -- Encapsulate physics event data.
    - [[CRingFragmentItem (v12)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r8251.md]] -- Encapsulate an event builder fragment.
    - [[CRingPhysicsEventCountItem (v12)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r8406.md]] -- Document trigger counts.
    - [[CRingScalerItem (v12)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r8608.md]] -- Encapsulate scaler data
    - [[CRingStateChangeItem (v12)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r8880.md]] -- Document changes in DAQ state.
    - [[CRingTextItem (V12)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r9103.md]] -- Encapsulate text list ring items.
    - [[CUnknonwFragment (v12)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r9301.md]] -- Fragment item that does not contain a ring item.
  - 4.5. [[Sample Program(s)|https://github.com/FRIBDAQ/docs/tree/main/daqformat/x9314.md]]
    - [[evtdump|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r9321.md]] -- Multi format event file dumper

- **List of Examples**
- 2-1. [[Generating a Physics item for NSCLDAQ-11|https://github.com/FRIBDAQ/docs/tree/main/daqformat/c49.md#AEN82]]
- 2-2. [[Using Factories to Make a Physics Item for NSCLDAQ-11|https://github.com/FRIBDAQ/docs/tree/main/daqformat/x115.md#AEN132]]
- 3-1. [[Using a Version Designator to Construct a Ring Item Factory:|https://github.com/FRIBDAQ/docs/tree/main/daqformat/c171.md#AEN191]]
- 3-2. [[Using ring format items to select a format factory|https://github.com/FRIBDAQ/docs/tree/main/daqformat/c171.md#AEN223]]
- 4-1. [[Using smart pointers with the v10 factory object|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r2708.md#AEN2725]]
- 4-1. [[Adding a body header extension|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r4523.md#AEN4593]]
- 4-1. [[Adding a body header extension|https://github.com/FRIBDAQ/docs/tree/main/daqformat/r6920.md#AEN6990]]

---

|  |  |  |
| --- | --- | --- |
|  |  | Next |
|  |  | Introduction |
