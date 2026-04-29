|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 8. Event Builder | Next |


---

# <a name="AEN5646"></a>8.4. Fragments and Data Format

As has already been discussed, the event builder does not deal with ring
      items. Instead it handles fragments. Fragments are generic and are
      purposefully independent of the ring item data format so that the event
      builder can work with any type of data format the same way. This section
      will describe a bit more about the fragment as is useful for the standard
      user.

## <a name="AEN5649"></a>8.4.1. Anatomy of a fragment

A fragment consists of a header and body just like the ring item. In the
        parlance of the event builder, though, the body is referred to as the
        payload. There are 4 elements in the fragment header a timestamp, source
        id, payload size, and barrier type. The layout of the entire fragment is
        as follows:

<a name="AEN5652"></a>**Table 8-1. Fragment header**

|  | Description | Size (bytes) |
| --- | --- | --- |
| Header | Timestamp | 8 |
| Source ID | 4 |
| Payload size | 4 |
| Barrier type | 4 |
| Payload | Data... | (Payload size) |

## <a name="AEN5678"></a>8.4.2. Output Format

The event builder outputs standard NSCLDAQ 11.0 ring items. For
        non-PHYSICS_EVENT items, the outputted items are the same are inputted.
        Basically, the fragment headers that were appended to them by the client
        are stripped off before the data is outputted.

The format of PHYSICS_EVENTS are a bit more interesting. For physics
        events, the event builder will create "built" events. A built event is
        just a standard PHYSICS_EVENT. However, the body is constructed of the
        correlated fragments. It begins with a 32-bit
        integer specifying the entire size of the body and the remainder is a
        series of one or more fragments. There is no information specifying how
        many fragments are present without processing the body. Because each
        fragment specifies its payload size, the user can compute how many
        fragments are present merely by traversing the body and keeping track of
        the number of bytes and fragments traversed. Once the entire number of
        bytes in the body have been traversed, the user will know how many
        fragments are present.

From experience, the built body seems to be hard for many people to get
        their head around. One of the confusing things is that the built event
        is a ring item filled with fragments whose payloads are
        *complete* ring items themselves. Most of the time,
        users are shielded from the details of the ring item header and body
        header and only see the body proper. The built ring item however
        makes these plainly visible. This leads to confusion because typically
        the body header in each embedded ring item and the fragment
        header will have likely have the same information. It will look like there are
        duplicates of the same information in the body. The timestamp sometimes
        appears three times, because the number in the body header and fragment
        header are usually derived from a number in raw data. Though this has
        caused some users to panic when trying to understand their data, it is
        typically the result of a misinterpretation. Don't be fooled.

To make all of this a bit more plain, a diagram of the
        built ring item's body is shown when it contains two fragments.

<a name="AEN5685"></a>**Table 8-2. Body of Built PHYSICS_EVENT**

| High-Level Description | Lower-Level Description | Size (bytes) |
| --- | --- | --- |
| Body size | Number of bytes in body | 4 |
| Fragment #0 | Fragment Header | 20 |
| Ring Item Header | 8 |
| Ring Item Body Header | 4 or 20 |
| Ring Item Body | Determined by Readout program and user |
| Fragment #1 | Fragment Header | 20 |
| Ring Item Header | 8 |
| Ring Item Body Header | 4 or 20 |
| Ring Item Body | Determinable by Readout program and user |

Be aware that this is the format regardless of whether you choose to
        correlate data or not. When the event builder is not correlating, i.e.
        not building, the built events will always hold only 1 fragment in the
        body.  Otherwise, there may be more than one fragment.

Finally, the built ring item will be produced with a body header, the
        above table shows the format immediately following the body header. The
        timestamp in the body header will be determined based on the timestamp
        protocol of the event builder. The protocol allows you to choose whether
        the entire built event is labeled with the earliest, latest, or average
        timestamp of the correlated fragments. Also, the source id will be set
        according to user preference.  This allows for multiple stages of event
        building to be accomplished.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| More detail on when the fragments are ouptutted | Up | Using the Event Builder With The Manager |
