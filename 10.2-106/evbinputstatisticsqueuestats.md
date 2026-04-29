|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="evb1_inputstatistics_queuestats"></a>EVB::inputStatistics::queueStats

<a name="AEN8887"></a>## Name

EVB::inputStatistics::queueStats -- Per queue input statistics widget

<a name="AEN8890"></a>## Synopsis

**package require EVB::inputStatistics
            **

**EVB::inputStatistics::queueStats window *?options?*
**

** *$window* updateQueue *source depth oldest output-count*
**

** *$window* clear
                **

** *$window* reset
                **

<a name="AEN8906"></a>## DESCRIPTION

Provides a widget that can dipslay per queue input statistics.
            This is an **EVB::utility::sortedWidget**, where
            each of the widgets is an
            **EVB::inputStatistics::queueDisplay** widget.

See [[r9424#evb1_utility_sortedwidget_title]] for information about
            the **sortedWidget** UI element.  See
            [[r8976#evb1_inputstatistics_queuedisplay_title]] for
            information about the **queueDisplay** widget.

<a name="AEN8916"></a>## OPTIONS



`-title`Provides a title for the widget.  This is displayed
                        on the upper margin of the widget.

`-lefttitle`Provides a title for the source id column of the
                        widget (leftcolumn).

`-righttitle`Provides a title for the column that contains the
                        queue display widgets (right column).

<a name="AEN8934"></a>## METHODS



**            EVB::inputStatistics::queueStats window *?options?*
**

Creates the widget.  The `window`
                            command parameter is the window name for the
                            top level of the widget hierarchy this creates.
                            This must not be the path to an existing widget.

If `options` are supplied, they
                            represent configuration options described in the
                            OPTIONS section above.

** *$window* updateQueue *source depth oldest output-count*
**

Updates the statistics in a queueDisplay widget.
                            `source` represents the data source
                            and selects which queueDisplay widget to update.
                            If there is no queueDisplay widget associated with
                            `source` a new one is made.

The remainder of the parameters are statistics
                            value to put in the widget. `depth`
                            is intended to be the number of fragments currently in
                            that queue.  `oldest` is intende to
                            be the timestamp of the fragment at the head of the queue
                            and `output-count` is intended
                            to be the number of fragments that have been removed
                            from the front of the queue (because they were sorted
                            and emitted to the output stage).

** *$window* clear
                            **

Zeroes the statistics on all of the output
                            queue widgets.  To zero a specific widget
                            use **updateQueue** and pass in 0
                            for all of the counter values.

** *$window* reset
                            **

Destroys all of the per queue statistics user interface
                            elements.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| EVB::inputStatistics::statusDisplay | Up | ::EVB::inputStatistics::queueDisplay |
