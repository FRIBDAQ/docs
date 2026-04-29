|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 9. EVBLite -  light event building | Next |


---

# <a name="AEN5816"></a>9.3. The evblite Tcl package.

EVBLite is a Linux pipeline.  The evblite Tcl package makes it easy to define, start and stop
      the EVBLite pipeline passing the **evbtagger** and **glom** programs
      any options required to make the function properly.  The evblite package can be used in the
      ReadoutCallouts.tcl script to automatically start the pipeline.  It is recommended
      that this be done in OnStart as the pipeline is persistent.

Here's a sample fragment from a ReadoutCallouts.tcl script that sets up and starts
      EVBLite when the system transitions from not ready to halted:

<a name="AEN5825"></a>**Example 9-1. Starting EVBLite from ReadoutCallouts.tcl**

```
package require evblite  
...
set evbInstance [evblite::evblite %AUTO% \
   -insid 0 -inring rawdata -outring builtdata -dt 1000] 
...
proc OnStart {} {
   ...
   $::evbInstance start                            
   ...
}
      
```

Let's deconstruct this step by step.  Note, however, that the example above
      assumes the script is running in an environment wich includes $DAQROOT/TclLibs in the  Tcl package
      search path.  This is the case in ReadoutCallouts.tcl.  When using the manager,
      the container initialization script can source an appropriate daqsetup.tcl
      and the program definition can define the TCLLIBPATH environment to be
      $DAQROOT/TclLibs.

[[x5816#evblite.require]]            Pulls the evblite package into the script.  This package defines a snit type;
            evblite::evblite to encapsulate each instance od EVBLite.  Note that running several EVBLite instances
            which, in turn, feed a second level event builder is perfectly reasonable.
        [[x5816#evblite.instance]]            This pair of lines define an event builder instance.
            In this case, the event builder is configured as it's instantiated.   It is also possibel to use
            the objects' `configure` subcommand to configure the event builder
            after instantiation.  Configuration is done using the option database.   The full set of options
            accepted by evblite objects can be found in the refrence pages.  We use:
        

-insid 0`-insid` specifies the input source id.  If non physics items are found
                     with no body header, this is the sourcde id that will be put in its fragment header.
                     Note; EVBLite requires that all physics items have body headers.

-inring rawdataSpecifies the ringbuffer (name not URL) that will be the source of data for
                     EVBLite.  If a remote ring is desired you can specify the proxy ring for the remote
                     ring in the localhost.

-outring builtdataSpecifies the name of the ringbuffer into which EVBLite will put built event data.
                     Ringbuffer producers must be local so the ring buffer is specified by name rather than
                     URL.

-dt 1000Specifies the event builder coincidence window.   Events will all lie in a time interval
                     where their timestamps will be at most 1000ticks larger than the initial fragment.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| evbtagger - making event builder fragments from ring items. | Up | ScalerDisplay |
