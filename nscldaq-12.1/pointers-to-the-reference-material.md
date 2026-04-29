|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 59. NSCL DAQ Thread Library | Next |


---

# <a name="AEN14368"></a>59.5. Pointers to the reference material

This section provides pointers to the reference sections.
            The following three classes define the public interfaces
            for the threading and synchronization library:



- [[r50896]]
                      is the abstract base class from which you can construct
                      application specific threads.
- [[r51134]]
                      is the class used to perform synchronization.
- [[r51242]]
                      is built on top of `Synchronizable` to 
                      provide monitor like synchronization semantics.
- [[r51683]]
                  documents condition variables.  Condition variables are a
                  synchronziation scheme that allows a thread to wait for a specific
                  condition to be signalled by another thread.
- [[r51994]]
  	      documents the `CGaurdedObject` base class.
- [[r52060]] described
                the `CBufferQueue` inter thread communications
                class.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Thread safe queues (CBufferQueue). | Up | Access control and security |
