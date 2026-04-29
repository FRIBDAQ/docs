|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 11. Using NSCLDAQ with a CAEN V785 Peak-Sensing ADC and CAEN V262 IO Register | Next |


---

# <a name="AEN6456"></a>11.4. The dumper program

When we run our program, we are going to want to inspect the data
          that is being read out from the hardware. To do this, we will use the
          **dumper** program. But first, we need to understand a
          little bit about a ring buffer (a.k.a. a "ring").

## <a name="AEN6460"></a>11.4.1. A very brief introduction to ring buffers

A ring buffer is a fundamental component of the system
            NSCLDAQ uses to pass data from one process to another and is where
            the readout program sends its data. Other processes can then read
            the data from that ring buffer. From the vantage point of the ring
            buffer, the program filling it with data is its
            *producer* and the programs that read from it
            are its *consumers*. There is only allowed to
            be a single producer per ring buffer while there may be many
            consumers.

Ring buffers are local to a specific computer but are accessible
            over the network. Each ring buffer is identified by a user-defined
            name and the hostname of the computer it is located on. When
            processes want to attach to a ring to either produce or consume
            its data, they must specify the name of the ring via a universal
            resource identifier (URI). The URI specifies the protocol
            (proto://), the hostname
            (host), and the name of the ring
            (name) as a single string:
            proto://host/name. When a user attaches to a
            ring on another computer, a service running in the background
            called RingMaster sets up the connection that
            will stream the data across the network for you. In this way, the
            nework is basically transparent.

## <a name="AEN6471"></a>11.4.2. Starting up the dumper program

The program provided by NSCLDAQ for consuming data from a ring
            buffer and printing it to a terminal is called
            **dumper**. It is probably the most fundamental
            diagnostic provided by NSCLDAQ and is incredibly useful in
            understanding the integrity of a Readout program. We will use it
            inspect the data outputted by our Readout program.

To start the **dumper** program, log onto any
            computer on the same network as the one physically connected to
            the VME crate in which your CAEN V785 has been installed.
            Typically this is the same machine, but it doesn't have to be.
            To launch the program, you have to specify the hostname of the
            computer running the Readout program and also the name of the
            ringbuffer to connect to. The default values for these are
            "localhost" and your username. Assuming the Readout
            program is running locally (i.e. hostname=localhost) and your user
            name is "user0", you would type either:

```
spdaqxx> dumper --source=tcp://localhost/user0
            
```

or equivalently,

```
spdaqxx> dumper
            
```

The dumper terminal session will probably start spewing stuff at
              to the console once the run starts at a rate that is unreadable. 
              It is generally useful then to limit
              the number of ring items processed by the dumper by passing the
              `--count` option. The value provided to this at
              launch determines the number of items to process before exiting.

You should now attach this to the ring buffer that will 
              contain your Readout program's output. Its name will default to
              your username. For illustration purposes, we once again assume
              your username is "user0". Here is how to tell the dumper program
              to dump the first 10 events that pass through it.

```
spdaqxx> dumper --source=tcp://localhost/user0 --count=10
            
```

If this failed with some output like this:

```
spdaqxx> dumper --source=tcp://localhost/user0 --count=10
Failed to open data source tcp://localhost/user0
No such file or directory
exiting
            
```

it just means that the ring buffer has not been created yet. You
              should create it and then start your dumper program again. Here is
              how you do that:

```
spdaqxx> ringbuffer create user0
spdaqxx> dumper --source=tcp://localhost/user0 --count=10
            
```

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Setting up the software | Up | Running the Readout Program |
