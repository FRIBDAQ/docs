|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 49. NSCL DAQ Thread Library | Next |


---

# <a name="AEN9746"></a>49.5. Pointers to the reference material

This section provides pointers to the reference sections.
            The following three classes define the public interfaces
            for the threading and synchronization library:



- [[r36196]]
                      is the abstract base class from which you can construct
                      application specific threads.
- [[r36434]]
                      is the class used to perform synchronization.
- [[r36542]]
                      is built on top of `Synchronizable` to 
                      provide monitor like synchronization semantics.
- [[r36983]]
                  documents condition variables.  Condition variables are a
                  synchronziation scheme that allows a thread to wait for a specific
                  condition to be signalled by another thread.
- [[r37294]]
  	      documents the `CGaurdedObject` base class.
- [[r37360]] described
                the `CBufferQueue` inter thread communications
                class.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Thread safe queues (CBufferQueue). | Up | Access control and security |
