|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 74. Event orderer and its user interface | Next |


---

# <a name="AEN15445"></a>74.4. Event orderer packages

This section describes the set of packages that make up the
            event builder application programming interface.  There are additional
            packages and interfaces that are considered internal and should not
            referenced by user code, as these interfaces are not guaranteed to
            be stable across different versions of the event orderer.

If you need something that is provided as an internal interface,
            ask about it so that a public interface can be added to meet your
            needs.  In this way your code is less likely to break as the
            event orderer evolves...

The remainder of this section is a list of the package names and
            a brief description of each package and the services or user
            interface elements it provides.



EVB::barriersProvides graphical user interface elements that can be
                        used to monitor barrier statistics.  Barriers are
                        sets of event fragments that collectively indicate some
                        sort of synchronization has occured between the data sources.

Each source is expected to contribute a barrier.
                        Barrier fragments also have a barrier type.
                        The user interfaces support the display of barrier
                        statistics in summary, by source as well as exceptional
                        cases such as barriers with mixed types and barriers
                        with sources that did not participate within the
                        fragment ordering timeout.

EVB::CallbackManagerThis package is not normally used by application code
                        but is a stable and usable interface.  It provides
                        a mechanism for registering a set of callback methods,
                        supplying scripts with substitutions and invoking
                        those callbacks with strings that will replace
                        the substitution strings.

A typical use-case would be to implement the callbacks in
                        a mega widget implemented in e.g. snit or itk.

EVB::connectionListProvides an auto-updating widget that displays the
                        set of connections to the event orderer by data source
                        clients.  For each client, the source node, the
                        connection description supplied at connection time, the
                        state and whether or not the connection appears stalled
                        are displayed.

EVB::GUIProvides several top level user interface elements that
                        can be used to implement a monitoring interface for
                        the event orderer.

EVB::inputStatisticsProvides user interface elements that support the display
                        of statistics describing the fragments received by
                        the event orderer from the data sources.

EVB::LateProvides user interface elements that allow applications
                        to display statistics on late fragments.  A late fragment
                        is one that is received sufficiently late in time that
                        when it is emitted it breaks the total ordering of timestamps
                        in the output fragments.

EVB::outputStatisticsProvides user interface elements that support the display
                        of output statistics.  In addition to displaying summary
                        statistics, these user interface elements can display the
                        output statistics by data source as well as the
                        *hottest* and *coldest*
                        sources. [[1]](#FTN.AEN15490)

EVBUtilitiesProvides some useful utility procs and classes.

EventBuilderProvides useful procs for starting the event orderer and
                        registering specific callbacks with the builder.

ObserverProvides a snit type that suppports the implementation
                       of the Observer pattern.  See e.g.
                       [http://en.wikipedia.org/wiki/Observer_pattern](http://en.wikipedia.org/wiki/Observer_pattern)
                       for a description of this pattern.

Note that contrary to what the wikipedia description of
                        this pattern might imply, the use of this sort of observer
                        is not restricted to object oriented constructions.

EVBOrdererThis package represents commands that influence the
                        action of the event builder compiled fragment handler
                        code. Note that many of the commands defined by this package
                        also have Tcl jackets.  Where this is true you should
                        use the jackets instead as they may take care of other
                        issues that may not be trivial to deal with.

### Notes

|  |  |
| --- | --- |
| [1] | The hottest data source is defined
                        as the one which has emitted the most fragments while
                        similarly the coldest data source is the one which has
                        emitted the fewest fragments. |

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Writing an event orderer startup script | Up | Event builder client framework |
