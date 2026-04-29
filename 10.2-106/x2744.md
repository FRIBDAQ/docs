|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 38. Format of Event Data In Ring Buffers | Next |


---

# <a name="AEN2744"></a>38.3. Incorporating the headers and libraries into your applications.

NSCL DAQ provides a class library that allows you to encapsulate
            ring buffer data items in objects from which you can get/set data.
            Ring buffer item objects are intended both for producers and consumers
            of data.  See the 3daq section of the reference material for
            detailed per class documentation.

Each class has a header file that is named the same as the
            class with a .h appended. Thus to incorporate
            the definitions for the
            `CRingItem` base class in your source code you would
            add the line:

<a name="AEN2750"></a>**Example 38-1. Including a ring item class **

```
#include <CRingItem.h>
            
```

To your source files.

At compile time you would need to add a -I switch
            to tell the compiler where these headers are.  If the
            environment variable
            DAQROOT
            points to the top level of the NSCLDAQ installation tree you might
            do this as shown below:

<a name="AEN2757"></a>**Example 38-2. Telling the compiler where to find Ring Item headers**

```
g++ -c -I$DAQROOT/include mymodule.cpp
            
```

At link time you need to provide the location of the libraries as
            well as to specify the set of libraries that must be included.
            Note that as the example below shows, normally using the
            data format library implies you will need the data flow library as well:

<a name="AEN2762"></a>**Example 38-3. Linking the ring item format libraries**

```
g++ -o myApplication src1.o src2.o ... -L$DAQROOT/lib \
        -ldataformat -lDataFlow -Wl,"-rpath=$DAQROOT/lib"
            
```

The following classes manage data formatting:



[[r20487]]Base class for all the ring data item format classes.
                        This class also has the static member
                        `getFromRing` which accepts a
                        ring object reference and a
                        `CRingSelectionPredicate` reference,
                        and returns a pointer to the next ring item that matches
                        the predicate's match criteria.

[[r21133]]Represents a state change item.  Given a reference to
                        a `CRingItem` (e.g. one just gotten
                        from `CRingItem`::`getFromRing`),
                        one of the constructors constructs an equivalent ring state change object or
                        throws a `std::bad_cast` exception
                        if the item is not a valid state change.

[[r20784]]Represents a state change item.  Given a reference to a
                        `CRingItem` one of the constructors
                        can produce a `CRingScalerItem` object
                        or throw a `std::bad_cast` exception
                        if the item was not actually a scaler item.

[[r21444]]Encapsulates a text list item.  As with all the above
                        classes, a constructor exists that converts a
                        `CRingItem` to a
                        `CRingTextItem` or throws a
                        `std::bad_cast` if that's not legal.

Note that there is no class encapsulation of an event as these are
            most conveniently manipulated via the
            `CRingItem` base class.

## <a name="AEN2806"></a>38.3.1. Generic ring data sources

You may want a program to work equally well when pointed at a 
              ring buffer and when pointed at a file of ring items, such as
              an event file created by the event logger.

A set of data source classes and a data source factory allow you
              to easily write program like this.  The key point is that 
              ring data sources are specified by uniform resource identifiers
              (URIs).  The first part of a URI is called the 'protocol' and
              defines how a connection takes place.  For online rings we have
              seen that the protocol is tcp:  For offline
              event files, the protocol is file:.

The data format library provides a generic base class;
              `CDataSource`.   Concrete subclasses include
              `CRingDataSource` and
              `CFileDataSource` provide data sources for
              online rings and offline files respectively.  The factory class
              is `CDataSourceFactory`.

The data sources return generic ring items.  These can be
                upcast into specific ring item types by using methods in the
                `CRingItemFactory` class.

Reference information on these classes is availabe at:
                [[r23559]],
                [[r23600]],
                [[r23668]],
                [[r23725]],
                and
                [[r23781]].

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Selecting Data From a Ring Buffer | Up | Creating ring items |
