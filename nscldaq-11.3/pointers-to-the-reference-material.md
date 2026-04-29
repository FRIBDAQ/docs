|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 51. NSCL DAQ Thread Library | Next |


---

# <a name="AEN10282"></a>51.5. Pointers to the reference material

This section provides pointers to the reference sections.
            The following three classes define the public interfaces
            for the threading and synchronization library:



- [[r37116]]
                      is the abstract base class from which you can construct
                      application specific threads.
- [[r37354]]
                      is the class used to perform synchronization.
- [[r37462]]
                      is built on top of `Synchronizable` to 
                      provide monitor like synchronization semantics.
- [[r37903]]
                  documents condition variables.  Condition variables are a
                  synchronziation scheme that allows a thread to wait for a specific
                  condition to be signalled by another thread.
- [[r38214]]
  	      documents the `CGaurdedObject` base class.
- [[r38280]] described
                the `CBufferQueue` inter thread communications
                class.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Thread safe queues (CBufferQueue). | Up | Access control and security |
