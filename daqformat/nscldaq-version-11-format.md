|  |  |  |
| --- | --- | --- |
| NSCLDAQ Unified Format Library |
| Prev | Chapter 4. Reference pages | Next |


---

# <a name="AEN4479"></a>4.3. NSCLDAQ version 11 format

**Table of Contents**[[r4523]] -- Create ring items in version 11 format.[[r5155]] -- Encapsulate version 11 ring items.[[r5443]] -- Encapsulate abnormal end run item.[[r5516]] -- Provide the format version of subsequent data[[r5603]] -- Document event builder parameters.[[r5748]] -- Encapsulate a physics event.[[r5828]] -- Encapsulate an event builder fragment.[[r5983]] -- Encapsulate trigger count ring item.[[r6185]] -- Encapsulate periodic scaler ring items.[[r6470]] -- Encapsulate state change ring items.[[r6694]] -- Encapsulate text strings.[[r6896]] -- Event buider fragments with non ringitem payloads.

This section contains reference information describing support for
            the version 11 format.  Version 11 introduced body headers to
            simplify event buiding.

A body header is an optional part of a ring item that has the following
            fields:



uint32_t `s_size`Contains the size of the body header.  Note that this
                        allows application specific data to be appended to the
                        body header as the formatting software uses this size
                        to determine both the presence of and size of this header.

If a `s_size` is larger than
                        sizeof(v11::BodyHeader) the body header
                        is said to have a *Body Header Extension*.

In version 11, if `s_size`
                        is 0, the item has no body header.

uint64_t`s_timestamp`The timestamp at which the item was produced. The units
                        of the timestamp are application defined, however
                        it is critical that all data sources have the same
                        timestamp units, the same source of timestamp increments,
                        and as close to the same zero time as electronically
                        possible.

uint32_t`s_sourceId`The data source.  Each data source is assumed, by
                        the event builder, to be totally time ordered.
                        The process of event building is, therefore, oneo f
                        merging the times from all data sources to produce
                        a single totally time ordered stream of fragments
                        and then gluing (glomming) together fragments
                        whose timestamps are within a specified coincidence
                        window.

Data sources must be unique and often, but not always,
                        identify a readout program.  As a counter example to this,
                        a VME crate with CAEN DPP Modules is readout with each
                        module as a separate data source.

uint32_t`s_barrier`NSCLDAQ's event builder provides for rough barrier synchronization
                        between data sources.  Barrier synchronization means that
                        no further data is emitted from a source within the event
                        builder until all sources have, a the head of their output
                        queues, a barrier item.

If `s_barrier`, is non-zero,
                        barrier synchronization is triggered.  The
                        `s_barrier` value may carry
                        additional information about why barrier synchronization
                        is underway.


As with all format versions an item factory is defined
            implementing the interface described by the abstract factory.
            Individual ring item type classes are also defined which
            implement interfaces that are defined by the abstract
            ring item type classes.  The remainder of this section
            provides reference information for these classes.

Note that all of the headers for the V11 format support
            are in the v11 subdirectory of the
            installation directory's include
            subdirectory.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CRingTextItem (v10) | Up | RingItemFactory (v11) |
