|  |  |  |
| --- | --- | --- |
| NSCL Ring buffer DAQ tutorial |
| Prev |  | Next |


---

# <a name="AEN18"></a>Chapter 1. Introduction

This guide provides tutorial and introduction material for NSCL
            researchers that needto convert their software from the NSCL
            Spectrodaq data acquisition system to the Ringbuffer data acquisition
            system.
            While the ring buffer data acquisition system (RingDaq) attempts to
            provide a high degree of source code compatibility with Spectrdaq
            data acquisition (SDAQ), there are some unavoidable differences.

As with SDAQ, the RingDaq provides a data acquisition framework into
            which experimenters must add a data source program (called Readout by
            convention), and an online analysis event unpacker (SpecTcl event
            processor(s)).  This guide shows you how to d create these components
            from scratch as well as from existing SDAQ components you may
            already have.
            Each chapter of this guide is intended to be nearly standalone, with
            supplemental material provided in the reference guide at
            [http://docs.nscl.msu/edu/daq/ringbuffer](http://docs.nscl.msu/edu/daq/ringbuffer).  This allows
            you to skip to the chapter that has the material you need next to
            get going:



- First I'll describe how to create a readout program from
                      scratch.
- Following that is material that describes how to convert an
                      existing SDAQ production readout program to a RingDaq
                      readout program.
- Next similar material is provided that describes how to
                      create and adaptor that allows you to use code that
                      you currently have to read data in SDAQ's readout classic
                      framework.
- Finally analyzing data from RingDaq with SpecTcl is described
                      along with the set of change you might have to make to
                      convert existing code from SDAQ to RingDaq.
- In addition to the main material, the first appendix
                      describes the format of data items that are put in the
                      ring by readout programs.
- The second appendix describes how to create user written
                      triggers.
- The third appendix describes a set of utilities that
                      allow you to plug spectrodaq analysis components into the
                      ringdaq system.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| NSCL Ring buffer DAQ tutorial |  | Creating a Readout program from scratch |
