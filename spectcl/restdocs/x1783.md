|  |  |  |
| --- | --- | --- |
| SpecTcl REST plugin |
| Prev | Chapter 3. REST requests supported. | Next |


---

# <a name="AEN1783"></a>3.29. Accessing the evbunpack command (new in 5.5)

Inreasingly experimental setups are made up of independent
                detector subsystems.  The NSCLDAQ event builder is then used
                to stitch together coincident event fragments into full
                experiment events.

It is convenient for the developer of each detector subsystem to
                indpendently build a software ecosystem to support their subsystem.
                It is equally convenient for the experiment integrator to be able
                to leverage parts of that ecosystem.  Specifically, each
                detector subsystem may have a well developed set of event
                processors for SpecTcl, and it would be very good to be
                able to drop those into a SpecTcl built to analyze the event built
                data.

The **evpunpack** command leverages event processing
                pipline support and internal SpecTcl classes to help do just that.
                Specifically, you can create event processors programmatically from
                registered event processing pipelines that are capable of
                unpacking data from the event builder.

URLs of the following form,

<a name="AEN1790"></a>**http://host:port/spectcl/evpunpack/create?name=evpname&frequencey=mhz&basename=treeparams;
                   **

Create a new unpacker for event builder data. The following
                are all mandatory query parameters:



nameName of the new event unpacker.  This will be registered
                        with the pipeline manager and, therefore, can participate
                        in pipelines created by that command/REST interface.

frequencyThe frequency of the event builder timestamp in MHz.
                        This is used to provide an elapsed run time that can
                        be used in creating diagnostic spectra from the
                        parameters the processor automatically creates.

basenameThe base name of the set of parameters the processor
                        makes.  For each event, the event processor fills in
                        several diagnostic parameters in addition to any the
                        pipelines attached to it produce:



`basename.event_no`The event number.

`basename.run_time`Elapsed run time based on the timestamp and
                                frequency, in seconds.

`basename.sources`Number of fragments in an event.

`basename.unrecognized_source`Number of sources in the event for which no
                                event processing pipeline was registered.

`basename.n_present`Flag to indicate source n was present.

The intent of these parameters is to provide support
                        for several standard event builder diagnostic spectra.

URLs of the following form:

<a name="AEN1838"></a>**http://host:port/spectcl/evbunpack/add?name=evbname&source=sourceid&pipe=pipe-name
                   **

Registers an event processing pipeline (either programmatically
                created or created using the pman command/REST interface) to
                process the event fragments from a specific event source.
                The data presented to the event processor is the same as if it
                were seeing data from a system that only took data from that
                subsystem.

The mandatory query parameter name is the
                name of the event processor being created.
                the mandatory query parameter source is the
                source id of the data that we are teaching it to process and
                pipe specifies the name of an event processing
                pipeline that will be invoked to process the data from
                fragments from the source.

URLs of the following form:

<a name="AEN1847"></a>**http://host:port/spectcl/evbunpack/list[pattern=*name-pattern*]
                   **

List the names of event processors that have been created via this
                command.  This is returned in the detail
                attribute of the returned object as an array of strings.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Accessing the pman comman (new in 5.5) | Up | Excuting arbitrary commands in SpecTcl (new in 5.5) |
