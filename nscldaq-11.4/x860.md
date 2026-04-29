|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 4. VMUSBReadout | Next |


---

# <a name="AEN860"></a>4.4. The Slow-Controls Subsystem

A fundamental limitation placed on the VM-USB is that only one process can
      communicate with it at a given time. This introduces a complication when
      trying to use separate programs for controlling devices that need only to
      be configured rather than read out. There many ways to deal with this
      issue, but the approach taken by VMUSBReadout is to turn the VMUSBReadout
      program into a proxy for other applications that might want to use the
      VM-USB. In another sense, the VMUSBReadout serves the VM-USB to other
      programs. This is accomplished via the slow-controls server that listens
      and accepts connections from clients who make remote requests to it. The
      port on which the server listens defaults to 27000 but can be defined by
      passing the `--port` command line argument to
      VMUSBReadout.

If the run is halted, the slow-controls server can directly manipulate the
      VM-USB to perform the desired device changes. If, however, the VMUSB is in
      data taking mode, the slow-controls server pauses the run, performs the requested 
      operation, and then resumes the run.  You should avoid working with control
      panels during production runs for that reason.

The configuration of the slow-controls subsystem is similar to that of
      the readout subsystem.  A configuration file, written in Tcl, defines the
      control modules present in the system. An important difference to the
      daqconfig.tcl file is that the controls configuration file is read only once
      when VMUSBReadout starts. For that reason, modules loaded into the
      slow-controls server are configured once at start up and do not change
      during the duration of VMUSBReadout.

The **Module** command is used to create, configure, and
      query the configuration of slow-controls devices known to the server. A
      set of prepackaged module types are provided by VMUSBReadout. Each created
      module must be given a unique name and is automatically registered to the
      server upon creation. When a client makes a request to the slow-controls
      server, it must provide the name of the client it wishes to handle its
      request. If no module with the name the client provides has been
      registered to the server, unexpected results are likely to occur as well
      as an error. For that reason, if you wish to use the slow-controls server,
      it is important that you register the module with the server first before
      using your client. Client requests either get, set, or update requests.

Up to this point, we have mostly discussed how the slow-controls server
      acts as a proxy for other client applications. However, the slow-controls
      subsystem also has some utility in its own right. For one, the
      **watch** command can be used to periodically poll devices
      for status without pausing data taking.  This is useful for monitoring the
      performance of devices over the coarse
      of data taking. The subsystem is also ideal for performing tasks that
      need to occur only once during a session or on demand. A good example of
      this is the loading of firmware. The vast majority of times, firmware only
      needs to be loaded once per power cycle. For this reason and the fact that
      it often takes a noticeable amount of time to complete, it makes little
      sense to do it every run. The slow-controls server is a good tool for
      this kind of operation because slow-controls modules each define an
      initialization procedure that is executed at start up or anytime
      thereafter via the **init** command.

Once again, it is simplest to illustrate how to set up the controls
      configuration script by example rather than in prose. For that reason we
      will proceed with a short example.

<a name="AEN872"></a>**Example 4-2. A Sample Controls Configuration**

In this example, we will set up the server to configure a Caen V812
        constant-fraction discriminator. The Caen V812 is a VME board that
        responds to commands addressed to it. The board that we are configuring
        has a base address of 0x12450000, which we will need to provide to the
        module we create. The type of module that understands how to work with
        the V812 has a module type of "caenv812" so we must pass that type as an
        argument to the **Module** command. To create the module and
        configure its from a file we add the following two lines to our
        ctlconfig.tcl script.

```
Module create caenv812 cfd
Module config cfd -base 0x1245000 \
        -file [file join [file dirname [info script]] cfd1.cofig]
      
```

That is it. The act of creating the module also registers it by the name
        cfd to the slow-controls server. At this point, a
        client application could in principle attempt to send it requests.

If a user wants to write their own module for the slow-controls subsystem,
      they can do so. There is a well-defined framework for developing these.
      You can learn more about creating your own modules at 
      [[x1616]].

## <a name="AEN881"></a>4.4.1. Using Remote Procedure Calls To Execute Stacks

There are numerous slow-controls modules availabe for use with the
        Module command (see [[r76559]]). Because of its
        usefulness, we will very briefly mention the "vmusb" module type. This
        module enables a client of the slow-controls server to execute arbitrary
        command stacks as remote procedure calls. This functionality must be
        enabled by including the following line in your control configuration
        file:

```
Module create vmusb ctlr
      
```

You can see that there is no magic here compared to the previous
        example. We have just created a new module named "ctlr" of type
        vmusb. This module type is the handler for the remote procedure calls
        and literally only knows how to execute lists and return the results.
        Clients that want to submit their remote requests then do so by using
        the following classes:



`CVMUSBReadoutList`Instances of this class represent lists of VME operations you want
              to perform via the server.  See [[r71619]] for reference
              information.

`CVMUSBRemote`Instances of this class represent connections to VMUSBReadout slow
              controls servers.  Instances provide a mechanism for submitting a
              `CVMUSBReaoutlist` for remote execution and
              gathering the results back for client code.

See [[r72524]]
              for reference information about this class.

Programs using these classes must link to the
        libVMUSBRemote library in the NSCLDAQ
        lib subdirectory.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Writing the Configuration Script | Up | Running the VMUSBReadout program |
