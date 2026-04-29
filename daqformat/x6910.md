|  |  |  |
| --- | --- | --- |
| NSCLDAQ Unified Format Library |
| Prev | Chapter 4. Reference pages | Next |


---

# <a name="AEN6910"></a>4.4. NSCLDAQ Version 12 format

**Table of Contents**[[r6920]] -- Create ring items formatted for version 12.[[r7555]] -- Encapsulate V12 undifferentiated ring item[[r7855]] -- Encapsulate abnormal end run item.[[r7928]] -- Document the version of NSCLDAQ format that follows[[r8016]] -- Document event builder parameters.[[r8164]] -- Encapsulate physics event data.[[r8251]] -- Encapsulate an event builder fragment.[[r8406]] -- Document trigger counts.[[r8608]] -- Encapsulate scaler data[[r8880]] -- Document changes in DAQ state.[[r9103]] -- Encapsulate text list ring items.[[r9301]] -- Fragment item that does not contain a ring item.

NSCLDAQ version 12 introduced two format changes relative to
            NSCLDAQ version 11:  The lack of a body header is denoted differently,
            Information is provided to trace back items whose body header source
            id was rewritten by the event builder back to their original source.

In NSCLDAQ-11, the ring item header is followed by either the
            size of a body header, if the item has  a body header, or zero
            if it does not.  A more consistent interpretation of the
            32 bit word following the header was adopted in version 12;
            The lack of a body header is indicated by a 32 bit word
            containing sizeof(uint32_t).  Thus skipping
            the body header, or lack of it, is handled consistently without
            a special case check for the lack of a body header.

It's important to know which readout program actually produced each
            item of data.  In version 11, e.g. scaler data had a source id in
            its body header but the event builder overwrites that to the source
            id it was told to emit (in case there is hierarchical event building).
            Many ring items in NSCLDAQ version 12 have an added original source id
            field.  The idea is that the originator can write its source id here
            as well as in the body header.

The original source id can then be used to determine which producer
            actually produced the item as it is immutable through the dataflow.

As with other concrete formats, the headers of the classes exported
            by this format are in a subdirectory of the includes installation
            directory.  In our case the subdirectory is v12.
            Furthermore, all classes and definitions are qualified by the
            v12 namespace to prevent collision with classes
            in other format.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CUnknownFragment (v11) | Up | RingItemFactory (v12) |
