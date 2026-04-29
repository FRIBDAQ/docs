|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 60. NSCL DAQ Thread Library | Next |


---

# <a name="AEN15371"></a>60.5. Pointers to the reference material

This section provides pointers to the reference sections.
            The following three classes define the public interfaces
            for the threading and synchronization library:



- [[r52381]]
                      is the abstract base class from which you can construct
                      application specific threads.
- [[r52619]]
                      is the class used to perform synchronization.
- [[r52727]]
                      is built on top of `Synchronizable` to 
                      provide monitor like synchronization semantics.
- [[r53168]]
                  documents condition variables.  Condition variables are a
                  synchronziation scheme that allows a thread to wait for a specific
                  condition to be signalled by another thread.
- [[r53479]]
  	      documents the `CGaurdedObject` base class.
- [[r53545]] described
                the `CBufferQueue` inter thread communications
                class.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Thread safe queues (CBufferQueue). | Up | Access control and security |
