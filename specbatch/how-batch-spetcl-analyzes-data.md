|  |  |  |
| --- | --- | --- |
| Batch SpecTcl (5.2 and later) |
| Prev | Chapter 2. Serial batch SpectTcl | Next |


---

# <a name="AEN192"></a>2.3. How Batch SpeTcl analyzes data

In normal SpecTcl you don't usually have to worry about
                data analysis works.  You click buttons on a GUI or use
                menu items and poof SpecTcl is analyzing data.
                In normal SpecTcl, what's happening under the hood is a multi-step
                process:



1. An **attach** command stops any
                           analysis in progress attaches SpecTcl to a new
                           data source (file or program on the end of a pipe).
2. The **ringformat** command is used
                           to indicate if the data source is NSCLDAQ-10.x or
                           NSCLDAQ-11.x (we're not going to consider data from
                           NSCLDAQ-8.x or earlier).
3. The **start** command is used to
                           start analyzing data from the data source.

What this all does is select data sources, and buffer
                decoding objects as well as start a Tcl event loop based
                scheme for analyzing data while keeping the user interface
                alive to your interactions.

Batch SpecTcl does not need to keep the user interface alive
                and has been written with NSCLDAQ-11.x data in mind (though
                a suitably sophisticated programmer can override that).

Batch SpecTcl provides an analysis scheme were data are taken
                from some data getting object and passed to some data distributing
                object.   In practice, the data getting object
                gets data from file while the data distributing object
                sends that data into the normal SpecTcl analysis objects.

To analyze data you must issue commands to select the
                data getter and the data distributor and then ask the
                program to analyze data.  While this may seem overly complex,
                when we discuss parallel SpecTcl, we'll see how this allows us to
                extend batch SpecTcl into an MPI application simply by
                adding additional data getters and distributors as well
                as a fancier script to drive the analysis.

The **filesource**  command specifies that the
                data getter the analysis will use gets data from a file.
                This command takes one mandatory parameter and an optional
                parameter.  The mandatory parameter is the name of the file
                the getter takes data from.  The optional one is the size in
                bytes of reads done from that file.  When you run parallel
                SpecTcl, this block size can have an impact on when you go
                I/O limited.  The default block size is 8192.

Here are some examples of the **filesource** command.

<a name="AEN214"></a>**Example 2-3. Using the **filesource** command**

```
filesource /mnt/evtdata/e00000/run6/run-0006-00.evt
filesource /mnt/evtdata/e00000/run6/run-0006-00.evt   [expr 1024*1024]
                
```

In the first example, data will be gotten from the run 6 event
                file in the evtdata area for some experiment using the default
                block size of 8192.  In the second example,
                The same file is read but with a block size of 1 Mbytes
                (1024*1024).

The analysis data distributor is selected using the
                **analysissink** command. It takes no parameters.

Once the getter and distributor are selected, you can begin
                analysis via the **analyze** command.
                This command will not return until the getter has indicated
                there's no more data available from its data source.
                Once that has happened, you're certainly free to analyze
                another run by using the **filesource**
                command to specify another file (for example you could analyze
                a segmented run in a loop over all the event files in the run).

Extending the **filesource** example above,
                here's how you would analyze the singly segmented run 6
                with a blocksize of 1Mbytes

<a name="AEN227"></a>**Example 2-4. Analyzing a run**

```
filesource /mnt/evtdata/e00000/run6/run6-0006-00.evt
analysissyink
analyze
                
```

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Commands supported by batch SpecTcl | Up | Creating a loadable package for the event analysis pipeline |
