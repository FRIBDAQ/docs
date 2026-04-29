|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 81. Support for CAEN Nextgen DPP-PHA digitizers | Next |


---

# <a name="sec.eventstruct"></a>81.3. Event structure

This section describes events written by the Readout program.
                These hits are encapsulated in NSCLDAQ ringitems.  When the event
                builder is  in use, additional event builder encapsulation
                will occur.

Ring items are described in the NSCLDAQ documentation.
                This is in the form of an annotated header for
                DataFormat.h.  See e.g.
                [https://docs.nscl.msu.edu/daq/newsite/nscldaq-11.3/r22906.html](https://docs.nscl.msu.edu/daq/newsite/nscldaq-11.3/r22906.html).
                In order to support event building, the ring items that encapslate
                hits include a body header.  The body header includes the hit timestamp
                and sourceid as well as a zero valued barrier type.

The additional event builder encapsulation is described in the
                NSCLDAQ section on the event builder e.g.
                [https://docs.nscl.msu.edu/daq/newsite/nscldaq-11.3/x4509.html](https://docs.nscl.msu.edu/daq/newsite/nscldaq-11.3/x4509.html)

This leaves to us documenting the format of the body of a hit:

<a name="AEN18490"></a>**Table 81-1. Format of event body**

| Data Type | Contents |
| --- | --- |
| uint32_t | Number of uint16_t's in the event |
| Variable. | Null terminated string that identifies the module |
| uint16_t | Channel within the module the hit came from |
| uint64_t | Hit timestamp in nanoseconds |
| uint64_t | raw timestamp only meaningful if selected |
| uint16_t | fine timestamp only meaningful if selected |
| uint16_t | Peak height (energy) |
| uint16_t | Low priority flags. Only meaningful if selected. |
| uint16_t | High priority flags. Only meaningful if selected. |
| uint16_t | Down sample selection code. Only meaningful if selected |
| uint16_t | Fail flags.  Only meaningful if selected |
| uint16_t | Analog probe type 1 - only meaningful if
                            analog probe 1 is selected for readout |
| uint32_t | Number of samples of analog probe 1 data.
                            This is zero if analog probe 1 is not selecte. |
| variable number of uint32_t values | Analog probe 1 values. |
| uint16_t | Analog probe type 2 - only meaningful if
                            analog probe 2 is selected for readout |
| uint32_t | Number of samples of analog probe 1 data.
                            This is zero if analog probe 2 is not selected. |
| variable number of uint32_t values | Analog probe 1 values. |
| uint16_t | Digital probe type 1 - only meaningful if digital probe 1 is selected |
| uint32_t | Number of samples in digital probe 1 |
| variable number of uint8_ts | Digital probe sample. |
| uint16_t | Digital probe type 2 - only meaningful if digital probe 2 is selected |
| uint32_t | Number of samples in digital probe 2 |
| variable number of uint8_ts | Digital probe sample. |
| uint16_t | Digital probe type 3 - only meaningful if digital probe 3 is selected |
| uint32_t | Number of samples in digital probe 3 |
| variable number of uint8_ts | Digital probe sample. |
| uint16_t | Digital probe type 4 - only meaningful if digital probe 4 is selected |
| uint32_t | Number of samples in digital probe 4 |
| variable number of uint8_ts | Digital probe sample. |

Note that if needed an additional byte will pad out the end of the
                event to bring it to an even number of uint16_t.
                However, since there are an even number of digital probes,
                all with the same length, I don't think this padding ever happens.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Getting Data | Up | Configuring SpecTcl |
