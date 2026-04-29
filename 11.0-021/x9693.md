|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 49. NSCL DAQ Thread Library | Next |


---

# <a name="AEN9693"></a>49.5. Pointers to the reference material

This section provides pointers to the reference sections.
            The following three classes define the public interfaces
            for the threading and synchronization library:



- [[r34824]]
                      is the abstract base class from which you can construct
                      application specific threads.
- [[r34958]]
                      is the class used to perform synchronization.
- [[r35056]]
                      is built on top of `Synchronizable` to 
                      provide monitor like synchronization semantics.
- [[r35475]]
                  documents condition variables.  Condition variables are a
                  synchronziation scheme that allows a thread to wait for a specific
                  condition to be signalled by another thread.
- [[r35776]]
  	      documents the `CGaurdedObject` base class.
- [[r35832]] described
                the `CBufferQueue` inter thread communications
                class.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Thread safe queues (CBufferQueue). | Up | Access control and security |
