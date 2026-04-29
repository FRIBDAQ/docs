|  |  |  |
| --- | --- | --- |
| NSCL Ring buffer DAQ tutorial |
| Prev |  | Next |


---

# <a name="AEN1077"></a>Chapter 4. Creating a Readout program from a spectrodaq classic readout program

There are still quite a few Readout programs that use the
            so-called *Readout Classic* framework.
            This chapter will show how to adapt these programs to use
            the RingDaq readout framework.

Here are the things you will need to do:



- Obtain the RingDaq Readout skeleton.
- Modify your skeleton.cpp and similar
                      files to change `DAQWordBufferPtr` objects
                      into uint16_t* objects and deal with the
                      fallout that causes.
- Write an adaptor event segment that wraps your
                      skeleton file into a RingDaq `CEventSegment`
- Write an adaptor scaler that wraps skeleton into a
                      RingDaq `CScaler`
- Modify the Skeleton.cpp to select
                      the event trigger, and register the event and scaler adaptors.
- Modify the Makefile to build the
                      software you need in addtion to the Skeleton.

# <a name="AEN1103"></a>4.1. Obtaining the RingDaq skeleton.

In this section we are going to operate as if an environment
                variable named DAQROOT is defined and
                points to the top level of the RingDaq distribution.
                At the time this is being written, at the NSCL this would give
                DAQROOT the value
                /usr/opt/daq/10.0.  As time goes on,
                this directory name may change as version numbers change.
                If you are not at the NSCL you will  need to contact your
                system administrators about where they installed this software.

The commands below show how to obtain a copy of the readout
                skeleton for RingDaq:

<a name="AEN1110"></a>**Example 4-1. Getting the skeleton**

```
mkdir myreadout
cd    myreadout
cp $DAQROOT/skeletons/sbs/* .
                
```

This sequence of unix shell commands creates a new directory
                named myreadout, makes that the current
                default directory and copies the readout skeleton into that
                directory.

The readout skeleton constists of the following files:



MakefileMakefile that builds the skeleton

Seleton.cppSource code for the registration code for the
                            readout framework.

Skeleton.hHeader defining the class implemented by
                        Skeleton.cpp

If you examine Skeleton.cpp you wont' find
                a main function.  This is because the readout
                framework is an application framework.  Application frameworks
                consist of a main program that is written for you and specific
                ways to register the presence of application specific code that
                needs to be called at well defined points in the program's
                execution.

Using an application framework frees you from having to worry about
                how your code actually interfaces with the data acquisition system,
                manager run-state transitions, trigger processing and so on.
                In the next two chapters we will see how to create code that is
                application specific and how to register it with the framework
                so that it is called when we want it to be called.

In this section we are going to operate as if an environment
                variable named DAQROOT is defined and
                points to the top level of the RingDaq distribution.
                At the time this is being written, at the NSCL this would give
                DAQROOT the value
                /usr/opt/daq/10.0.  As time goes on,
                this directory name may change as version numbers change.
                If you are not at the NSCL you will  need to contact your
                system administrators about where they installed this software.

The commands above just copy the skeleton, most likely you will
                want to also bring the source code for your existing readout into
                this directory as well.  Suppose these are located in the
                directory pointed to by the environment variable oldrdo:

<a name="AEN1143"></a>**Example 4-2. Adding existing readout files:**

```
mv Makefile Makefile.ring
(cd $oldro; tar czf - .) | tar xzf -
mv Makefile Makefile.original
mv Makefile.ring Makefile
                
```

These commands assume you may need to copy a directory tree.
                First the ringdaq Makefile is saved to Makefile.ring.
                Second the directory tree at oldrdo is copied
                via a tar pipeline.  Third the Makefile
                *this* copied in is saved as
                Makefile.original. Finally the ringdaq Makefile
                is restored from Makefile.ring

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Modifying theMakefile |  | Modifications to skeleton.cpp |
