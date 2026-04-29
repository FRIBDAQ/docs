|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="evbapi_chap"></a>Chapter 41. 
        Event builder client API

The NSCL Event builder is made of of two distinct stages.  These
        stages:



1. A fragment orderer which accepts chunks of event,
                       or *fragments* from the data sources
                       and produces as output fragments that are ordered
                       by timestamps that are associated with the fragments.
2. A builder stage that clumps event fragments with timestamps
                       that are within a coincidence window into events.


# <a name="AEN8639"></a>41.1. C++ Client API

This section provides tutorial information that describes the
            client C++ API to the event orderer/builder.
            [[r23546]]
            provides reference material for the class we are discussing here.

The interface is encapsulated in a single class named
            `CEventOrderClient`.  In the remainder of this
            chapter we will describe:



- [[x10543]]
- [[x8677]]

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Creating ring items | Up | Incorporating the event builder client library |
