|  |  |  |
| --- | --- | --- |
| NSCLDAQ Unified Format Library |
| Prev |  |  |


---

# <a name="AEN9321"></a>evtdump

<a name="AEN9325"></a>## Name

evtdump -- Multi format event file dumper

<a name="AEN9328"></a>## Synopsis

**evtdump *option...*
**

<a name="AEN9332"></a>## DESCRIPTION

The evtdump example is a multi-format event dumper.  At the
                    time it is being documented, it can properly dump data
                    from any of NSCLDAQ v10, v11, and v12 formats.  It does,
                    however, rely on the user to know the actual event format
                    and provide it to the program, if necessary through the
                    `--format` command line option.

The program uses this format to select a ring item factory.
                    It uses the factory selected by that data format to
                    acquire undifferentiated ring items from the data source.
                    The type of each ring item is analyzed and the factory is
                    again used to create the differentiated ring item.
                    Finally the `toString` method
                    of the differentiated ring item is used to create the output
                    for the dump of each ring item.

Options allow the front part of a data source  to be skipped,
                    as well as to  limit the number and types of ring items output.
                    The gengetopt program is used to generate
                    a command line processor and the options accepted by the
                    program from the file dumperargs.ggo.
                    See [https://www.gnu.org/software/gengetopt/gengetopt.html](https://www.gnu.org/software/gengetopt/gengetopt.html)
                    for information on gengetopt - in case you want to use
                    evtdump as a starting point
                    for another program.

<a name="AEN9343"></a>## OPTIONS

Note that each option has a short as well as a long form.
                    Only the long form is documented here.  See
                    `--help` if you want to see the
                    correspondence between short and long options.



`--help`Displays a brief help message that describes the program
                            and its options.  After printing the help information,
                            the program exits regardless of the remaining options
                            provided.

`--version`Prints the version of the program and exits.

`--source`The argument to this option is the source of data
                            to be dumped.  The program accepts URIs with
                            protocols file, to read data
                            from files.  ring and
                            tcp to read data from a ring buffer.
                            The program also accepts the special source specification
                            - which specifies that the program will
                            read data from its standard input.

Note that for tcp and
                            ring protocols (the two are
                            synonymous), the host part of the URI specifies the host in which
                            the ringbuffer lives while the path part of the URI is the
                            name of the ringbuffer in that host.
                            Hosts like localhost or one of
                            the host names assigned to the system will prevent the
                            establishment of a proxy ring buffer and hoisting pipeline
                            and take data from a local ringbuffer.

`--skip`The parameter to this option must be a non-negative integer.
                            The specified number of items from the data source,
                            regardless of type, will be ignored by the program
                            Once the `--skip` count items have been
                            skipped, normal processing will begin.

`--count`The paramter to this option must be a non-negative integer.
                            This parameter specifies the number of items that will
                            be dumped.  Once that number of items have been dumped,
                            the program will exist normally.

Note that number of items dumped takes into account
                            the item types on the `--exclude`
                            list.  This means that options on the exclude list will
                            not count against the `--count`.

`--exclude`The value of this option is a comma separated
                            list of strings that specify ring item types that
                            will not be dumped.  Valid values for the strings are:
                            BEGIN_RUN, END_RUN,
                            PAUSE_RUN, RESUME_RUN,
                            ABNORMAL_ENDRUN, PACKET_TYPES,
                            MONITORED_VARIABLES,
                            RING_FORMAT,
                            PERIODIC_SCALERS,
                            INCREMENTAL_SCALERS,
                            TIMESTAMPED_NONINCR_SCALERS,
                            PHYSICS_EVENT, PHYSICS_EVENT_COUNT,
                            EVB_FRAGMENT, EVB_UNKNOWN_PAYLOAD
                            and EVB_GLOM_INFO.

Note that TIMESTAMPED_NON_INCR_SCALERS
                            can only be present in a subste of NSCLDAQ version 10
                            data.  Furthermore the v10 INCREMENTAL_SCALERS
                            type is identical to the PERIODIC_SCALERS
                            of later versions.

`--scaler-width`Represents the number of bits of width in the scaler
                            data.  This may be needed if data from scaler modules
                            are less than 32 bits wide and may have non-zero
                            bits in the top part of the 32 bit scaler data in the
                            ring item.  Data from e.g. the CES CBD-8210
                            and the WIENER VC32/CC32  CAMAC controllers are
                            examples of this as CAMAC scalers are inherently
                            24 bits wide and these controllers place the
                            dataway Q and
                            X responses in the top two bits
                            of the 32 bit word they return.

If omitted the default is 32.

`--format`The parameter of this options is the NSCLDAQ
                            format version the data are assumed to be in.
                            This can be one of v10,
                            v11 or
                            v12 at this time.

This parameter defaults to v12.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home |  |
| Sample Program(s) | Up |  |
