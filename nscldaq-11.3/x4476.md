|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 7. Event Builder | Next |


---

# <a name="AEN4476"></a>7.2. Using the event builder

In NSCLDAQ, the standard way to set up the event builder is to use the
      ReadoutGUI. At the moment, the ReadoutGUI provides support for the event
      builder through the ReadoutCallouts.tcl script. You can learn more about
      this script in the ReadoutGUI section of the manual, but for this
      situation you only need to know that it is a Tcl script that is sourced by
      the ReadoutGUI when starting up. We can use it to enable the event builder
      and configure it for use. The recommended method for
      setting this up is to use the event builder callout bundle. Doing so
      reduces the amount of Tcl that needs to be added and ensures that the
      event builder recovers properly from errors. Simply add the following few
      lines to your ReadoutCallouts.tcl script:

```
package require evbcallouts

::EVBC::useEventBuilder

proc OnStart {} {
  ::EVBC::initialize i-restart false -glombuild true -glomdt 123 -destring evbout
}
    
```

When the "Start" button is pushed in the ReadoutGUI, this will add a set
      of controls for the event builder to the bottom of it. The option values
      provided here specify that the event builder will not restart on each new
      run (-restart), event correlation will be enabled (-glombuild), events
      within 123 clock ticks of each other will be correlated (-glomdt), and the
      output will be put into the ring named evbout on localhost.  If you prefer
      to change any of these parameters, feel free to do so. You can read more
      details about the callouts in the [[c11415]] as well
      in the [[r56539]].

The next thing that you need to do is register clients
      to the event builder, more specifically the event orderer. Assuming that
      the data being committed to the event builder are ring items, the client
      will be the ringFragmentSource. There is a convenience API call
      provided to assist in registering the ringFragmentSource called
      EVBC::registerRingSource. We will make use of it. The first consideration we have to make concerns the timestamps on the data we submit to the event builder. If the data that the ringFragmentSource is reading in already has a timestamp in its body header, then there is nothing to do. Otherwise, a
      timestamp extractor library must be created to instruct the program on how to extract timestamp from the data.
      A timestamp extractor library contains a function that will define how to extract a
      timestamp from the body of a PHYSICS_EVENT item. You can find an example
      of how to create one at the [[x11322]].

The EVBC::registerRingSource proc has the form:

```
::EVBC::registerRingSource sourceURI tstamplib ids info ?expectHeaders? ?oneshot? ?timeout? ?timeoffset?
    
```

where sourceURI is the full URI specifying the ring
      buffer to read data from, tstamplib is the path to the
      compiled timestamp extractor library, ids is the list
      of acceptable source, info is a string that describes
      the data stream, expectHeaders is a boolean value that
      tells the ringFragmentSource to allow for an absent timestamp extractor
      library because all ring items will have a timestamp already,
      oneshot is a boolean that when causes the
      ringFragmentSource to exit after it processes a complete run,
      timeout is the number of seconds to wait after the
      first ringFragmentSource has observed an end run item, and
      timeoffset is a value the user can provide to add to
      the timestamp to compensate for synchronization offsets. One very
      important timesaver is to set the expectHeaders option
      to true and then pass an empty string to tstamplib if
      you know that the Readout program you are using has already provided a
      timestamp to your data.  To illustrate how this works, consider an
      experiment in which the data produced by some silicon detectors are read
      out by a single Readout program in the system. The outputted data from
      this Readout are put into the "sidet0" ring buffer on localhost, and all
      of the data are already timestamped upstream. Being the first client
      registered, we choose to label this stream of data with source id 0. We
      also want to associate a human readable description of ?Si Dets? with it.
      In this scenario, the line that would be added to the ReadoutCallouts.tcl
      would be

```
 
        ::EVBC::registerRingSource tcp://localhost/sidet0 {} 0 "Si Dets" 1 1 20 0 
      
```



      If instead, the data were not already labeled with a timestamp and a
      timestamp extractor function was defined in the libtstamp.so shared
      library, the invocation would be. 
 
      ```
        ::EVBC::registerRingSource tcp://localhost/sidet0 /path/to/libtstamp.so 0 "Si Dets" 0 1 20 0
      
```


Putting this all together you would have a ReadoutCallouts.tcl that might look
      like this:

```
package require evbcallouts

::EVBC::useEventBuilder

proc OnStart {} {
  ::EVBC::initialize -restart false -glombuild true -glomdt 123
}

EVBC::registerRingSource tcp://localhost/sidet0 {} 0 "Si Dets" 1 1 20 0
    
```

Be aware that you need to add a registerRingSource line for every client
      that will be submitting data to the event builder.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Event Builder | Up | More detail on when the fragments are ouptutted |
