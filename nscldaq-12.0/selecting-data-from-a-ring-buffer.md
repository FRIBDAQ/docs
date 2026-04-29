|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 45. Data Format Support Software | Next |


---

# <a name="AEN11128"></a>45.2. Selecting Data From a Ring Buffer

Many data consumers are not interested in all of the
      item types that could be put in a ring buffer.   This section
      describes the infrastructure for selecting subsets of the data
      from ring buffers that are formatted as described in this chapter.

The ring buffer low level access library provides
      two powerful mechanisms for manipulating ring buffers based
      the concept of *predicates*.
      A predicate is a function that implement the
      `operator()` method in a way that it returns
      a bool.
      Predicate objects can therefore be thought of as functions that can
      have state that persists between calls.

`CRingBuffer` has two member functions
      `blockWhile` which periodically
      invokes a predicate until it returns false
      blocking for a settable time period between calls, and for a
      maximum timeout.
      `While` which simply repeatedly calls
      a predicate until it returns false.
      (like `blockWhile` but without blocking
      between calls to the predicate.

Armed with predicates, these two member functions an an understanding
      that items in the ring will have the item format described in the
      previous section, it is possible to implement a scheme for selectively
      obtaining data from a ring buffer.

The base class for this selectivity is
      `CRingSelectionPredicate`
      defined in
      CRingSelectionPredicate.h.  It provides
      base classes with the capability of specifying a list of item types
      called a *selection  map*.  Elements of this
      map consist of an item type and a flag.  The virtual function
      `selectThis` is given an item type peeked from
      the ring buffer and returns false if the item
      is acceptable.  Unacceptable items are skipped, and true is returned
      so that `While` continues to loop.

If `selectThis` returns true, the framework
      insepcts the type's flag.  If false, the predicate as a whole
      returns true. I false, the predicate skips the item if it is not
      the last one in the ring.

Two pre-packaged specific derivations of
      `CRingSelectionPredicate` have been built.
      In
      `CDesiredTypesPredicate`, any type not in the
      list is assumed to be undesirable and skipped.   In
      `CAllButPredicate`, the list of types define
      exceptiosn to the rule that all items are desired without sampling.
      Items in the list with the sample flag false, are assumed to be
      undesirable and are skipped.  items in the list with the sample flag
      true, are assumed to be wanted but only in sample mode.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Data Format Support Software | Up | Incorporating the headers and libraries into your applications. |
