|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 3. NSCLDAQ Data Format : The Ring Item | Next |


---

# <a name="AEN212"></a>3.2. The Body Header

Beginning with NSCLDAQ version 11.0, the ring item body has been modified
      to allow it to include timestamp, event source, and barrier information
      either emitted by or intended for the event builder.  This header follows
      immediately after the ring item header but is optionally present. If it is
      not present, there is a single 32-bit integer whose value is zero to
      indicate no body header is present. Otherwise, it is present. The
      structure of the body header is as follows:

<a name="AEN215"></a>**Table 3-2. Body Header**

| Description | Size (bytes) |
| --- | --- |
| Size | 4 |
| Timestamp | 8 |
| Source ID | 4 |
| Barrier Type | 4 |

The fields of this structure are as follows:



SizeThe inclusive size in bytes. You can also think of items that don't have
            a body header as having a header size of zero.  We promise to
            maintain backwards compatility by adding any new elements to the end
            of the body header.

TimestampThe value of the event/globally synchronized timestamp at the time
            this ring item was initially formed.

Source IDUnique identifier of the source of this ring item.

Barrier typeIf the item was part of a barrier synchronization amongst the data
            sources, this field will be non-zero and represent the type of the
            barrier.  If zero, this item was not part of a barrier.

To be even more explicit, the format of a complete ring item with a body
      header present is as follows:

<a name="AEN254"></a>**Table 3-3. Ring Item With Body Header**

|  | Description | Size (bytes) |
| --- | --- | --- |
| Header | Inclusive Size | 4 |
| Type | 4 |
| Body Header | Size = 20 | 4 |
| Timestamp | 8 |
| Source ID | 4 |
| Barrier Type | 4 |
| Body | Data... | >=0 |

Alternatively, the complete ring item without a body header present looks
      like the following:

<a name="AEN288"></a>**Table 3-4. Ring Item Without Body Header**

|  | Description | Size (bytes) |
| --- | --- | --- |
| Header | Inclusive Size | 4 |
| Type | 4 |
| Body Header | Size = 0 | 4 |
| Body | Data... | >=0 |

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| NSCLDAQ Data Format : The Ring Item | Up | The Ring Item Types |
