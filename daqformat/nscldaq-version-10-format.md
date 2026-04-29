|  |  |  |
| --- | --- | --- |
| NSCLDAQ Unified Format Library |
| Prev | Chapter 4. Reference pages | Next |


---

# <a name="AEN2702"></a>4.2. NSCLDAQ version 10 format

**Table of Contents**[[r2708]] -- Generate v10 ring item objects.[[r3350]] -- Version 10 ring item class.[[r3462]] -- Event builder fragment[[r3609]] -- Encapsulate trigger count ring item.[[r3787]] -- Encapsulate a scaler counts ring item.[[r4075]] -- Encapsulate run state change ring items.[[r4291]] -- Encapsulate a set of textual strings

Version 10 of NSCLDAQ is the earliest version of NSCLDAQ that used
            ringbuffers and ring items for data flow.  As  such, its data
            format is the most primitive.  Version 10 does not support body headers.
            Event building in NSCLDAQ 10  motivated the addition of body headers
            in later versions.

The version 10 headers are in the v10 subdirectory of the installation
            headers.  Furthermore all classes and definitions live in the
            v10 namespace.  The v10/DataFormat.h
            header provides formatting data and structs for the NSCLDAQ version
            10 internals.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Reference pages | Up | RingItemFactory (version 10) |
