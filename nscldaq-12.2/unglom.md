|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="daq1_unglom"></a>unglom

<a name="AEN22536"></a>## Name

unglom -- Break up an event file into event fragments

<a name="AEN22539"></a>## Synopsis

**unglom *?options?*
**

<a name="AEN22543"></a>## DESCRIPTION

**unglom** is a filter that accepts an event
                file on its standard input and produces and event file on
                its standard output.

The input event file is assumed to have come from the output
                of
                [[r22336]] in event
                building mode.  The output event file will be decomposed back into
                the original event fragments that made up the events built by
                [[r22336]].

Normally **unglom** will be a stage in a pipeline
                that will rebuild events using a different time value for the
                coincidence window than originally used to build the event file.

<a name="AEN22552"></a>## OPTIONS



`--help`All other options are ignored and brief program usage
                        help is output to stdout.  The program then exits without
                        processing stdin.

`--version`All other options are ignored and the program version is
                        printed to stdout.  The program then exits without
                        processing stdin.

`--id`=*non-event-fragment-id*Pre NSCLDAQ-11.0, and NSCLDAQ-11.0 and alter data that
                        do not have body headers,
                        non-event fragments do not have information
                        about their source-ids.  The value of this option is used
                        as the source id for non-event fragments in that case.
                        For NSCLDAQ-11.0 data, if the non-event fragments have a
                        body header, the event source in that header is used as
                        the fragment id instead.

<a name="AEN22571"></a>## EXAMPLES

The example below converts a glommed event file named
                run-0001-00.evt
                into a glommed event file named
                run-0001-00-dt=100.evt where the coincidence
                interval is 100 clock ticks.  Any non event
                fragments that don't have an id are given the source id 0.

<a name="AEN22577"></a>```
unglom <run-0001-00.evt --id=0 | glom --dt=100 >run-0001-00-dt=100.evt
                
```

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| ringFragmentSource | Up | ScalerDisplay |
