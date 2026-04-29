|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="evbapi_chap"></a>Chapter 52. 
        Event builder client API

The NSCL Event builder is made of of two distinct stages.  These
        stages:



1. A fragment orderer which accepts chunks of event,
                       or *fragments* from the data sources
                       and produces as output fragments that are ordered
                       by timestamps that are associated with the fragments.
2. A builder stage that clumps event fragments with timestamps
                       that are within a coincidence window into events.


# <a name="AEN14316"></a>52.1. C++ Client API

This section provides tutorial information that describes the
            client C++ API to the event orderer/builder.
            [[r40497]]
            provides reference material for the class we are discussing here.

The interface is encapsulated in a single class named
            `CEventOrderClient`.  In the remainder of this
            chapter we will describe:



- [[x16750]]
- [[x14354]]

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Manager User Interface API | Up | Incorporating the event builder client library |
