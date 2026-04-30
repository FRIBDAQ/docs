[← Preface](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/f4424.md) | [Home](https://github.com/FRIBDAQ/docs/tree/main/Home.md) | [libraries →](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/p1389.md)

---

<a name="AEN1"></a># <a name="AEN1"></a>NSCL DAQ Software Documentation


---

- **Table of Contents**
- I. [introduction](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/p3.md)
  - 1. [Introduction](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c5.md)
    - 1.1. [How does the ring buffer data acquisition system work](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c5.md#AEN15)
    - 1.2. [Overview of ring buffer utilities](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x123.md)
    - 1.3. [Documentation roadmap](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x180.md)
- II. [commands](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/p263.md)
  - 2. [The **ringbuffer** command](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c265.md)
  - 3. [Ring piping utilities](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c292.md)
  - 4. [Command line access to CAMAC via the SBS interface](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c318.md)
  - 5. [Tcl access to the VME via the SBS interface](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c342.md)
    - 5.1. [Incorporating Vme Tcl in your scripts](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c342.md#AEN357)
    - 5.2. [Sample programs that use the package](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x377.md)
- III. [utilities](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/p384.md)
  - 6. [glom](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c386.md)
  - 7. [Readout GUI (ReadoutShell)](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c397.md)
    - 7.1. [Running and using the ReadoutShell](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c397.md#AEN411)
    - 7.2. [Event file organization](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x479.md)
    - 7.3. [Customizing Readout Shell](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x513.md)
  - 8. [Epics Channel logging](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c656.md)
  - 9. [Providing EPICS channel information to Tcl Servers](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c669.md)
  - 10. [The epics display utility](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c707.md)
  - [epicsdisplay
          NSCLRingDAQ
  10.0+
          Ron Fox](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r726.md) -- Display epics channels
  - 11. [cratelocator](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c806.md)
  - 12. [CAEN V812 Constant Fraction Discriminator](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c819.md)
  - 13. [N568B CAENnet shaping amplifier](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c856.md)
  - 14. [VHS-40xxx SBS support.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c891.md)
  - 15. [The tcl server application](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c926.md)
  - 16. [Dumping events from ringbuffer or from file](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c945.md)
    - 16.1. [Item dump formats and examples](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c945.md#AEN973)
  - 17. [Compatibility utilities](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1009.md)
    - 17.1. [Format conversion with compatibilitybuffer](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1009.md#AEN1022)
    - 17.2. [Writing event files with compatibilitylogger](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x1046.md)
    - 17.3. [Convenience scripts](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x1065.md)
    - 17.4. [BufferToRing](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x1100.md)
  - 18. [daqstart - Starting programs with logging and monitoring](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1105.md)
  - 19. [DvdBurner - Using Tcl to burn runs to DVD](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1128.md)
  - 20. [Utilities for burning data to DVD](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1153.md)
  - 21. [The Event log program](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1164.md)
  - 22. [The ringselector application](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1194.md)
  - 23. [Scaler Display Software.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1269.md)
  - 24. [The Scaler Display Client](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1288.md)
  - 25. [Sequencing runs](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1299.md)
    - 25.1. [Configuring the sequencer.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1299.md#AEN1304)
    - 25.2. [Using the sequencer.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x1369.md)
- IV. [libraries](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/p1389.md)
  - 26. [Integer byte order conversion library](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1391.md)
    - 26.1. [Using the conversion library in your code](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1391.md#AEN1398)
    - 26.2. [Byte order signatures and conversion blocks](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x1415.md)
    - 26.3. [Data conversion](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x1435.md)
  - 27. [Ring master class library.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1472.md)
  - 28. [Networked ring buffer access](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1492.md)
  - 29. [Ring Buffer Primitives](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1553.md)
    - 29.1. [Incorporating ring buffer software](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1553.md#AEN1567)
    - 29.2. [Overview and Examples of ring buffers in action.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x1590.md)
  - 30. [The Tcl ring package](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1673.md)
  - 31. [The NSCL Exception class library](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1688.md)
    - 31.1. [Incorporating the library in your programs](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1688.md#AEN1709)
    - 31.2. [Exception classes](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x1719.md)
  - 32. [Shared memory](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1749.md)
    - 32.1. [Overview of the API, and using it from within your C++ software](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1749.md#AEN1762)
    - 32.2. [Compiling/Linking your software with the shared memory API](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x1820.md)
  - 33. [Access control and security](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1839.md)
    - 33.1. [Incorporting the software into your code](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1839.md#AEN1845)
    - 33.2. [Authenticators](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x1859.md)
    - 33.3. [Interactors](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x1904.md)
  - 34. [C++ encapsulation of a Tcl API subset](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1972.md)
  - 35. [NSCL DAQ Thread Library](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c2030.md)
    - 35.1. [The thread and synchronization model](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c2030.md#AEN2040)
    - 35.2. [Incorporating the library into an application.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2131.md)
    - 35.3. [Pointers to the reference material](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2142.md)
  - 36. [Parsing and URIs](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c2159.md)
  - 37. [Event builder client API](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c2217.md)
    - 37.1. [C++ Client API](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c2217.md#AEN2226)
    - 37.2. [Incorporating the event builder client library](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2240.md)
    - 37.3. [Connecting to the event builder.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2264.md)
    - 37.4. [Disconnecting from the event builder.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2297.md)
    - 37.5. [Sending data to the event builder.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2315.md)
    - 37.6. [The Event orderer/event builder API](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2405.md)
    - 37.7. [Callbacks](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2439.md)
  - 38. [Format of Event Data In Ring Buffers](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c2475.md)
    - 38.1. [The basic data formats](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c2475.md#AEN2489)
    - 38.2. [Selecting Data From a Ring Buffer](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2716.md)
    - 38.3. [Incorporating the headers and libraries into your applications.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2744.md)
    - 38.4. [Creating ring items](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2825.md)
  - 39. [S800 ReadoutCallouts](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c2862.md)
    - 39.1. [S800 Data acquisition system](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c2862.md#AEN2865)
    - 39.2. [Scope of the integration problem.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2872.md)
    - 39.3. [Using the S800 integration package](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2888.md)
  - 40. [The NSCL Exception class library](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c2929.md)
    - 40.1. [Incorporating the library in your programs](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c2929.md#AEN2950)
    - 40.2. [Exception classes](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2960.md)
  - 41. [C++ encapsulation of a Tcl API subset](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c2990.md)
  - 42. [The NSCL Exception class library](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3048.md)
    - 42.1. [Incorporating the library in your programs](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3048.md#AEN3069)
    - 42.2. [Exception classes](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x3079.md)
  - 43. [C++ encapsulation of a Tcl API subset](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3109.md)
  - 44. [SBS Base interface classes to the VME](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3167.md)
    - 44.1. [The classes](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3167.md#AEN3181)
    - 44.2. [Incorporating headers and libraries into your program.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x3238.md)
  - 45. [Tcl CAENet package](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3251.md)
  - 46. [The CES CBD 8210 Tcl CAMAC Package](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3292.md)
    - 46.1. [Incorporating camac into your scripts](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3292.md#AEN3304)
    - 46.2. [An overview of the use of the camac package](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x3323.md)
  - 47. [The Wienercamac Tcl package](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3342.md)
    - 47.1. [Incorporating wienercamac in your scripts.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3342.md#AEN3356)
    - 47.2. [Using wienercamac](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x3388.md)
  - 48. [SBS VME Module level device support software](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3530.md)
- V. [servers](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/p3542.md)
  - 49. [The RingMaster server](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3544.md)
    - 49.1. [The RingMaster Protocol](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3544.md#AEN3557)
  - 50. [Service Port Manager.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3695.md)
- VI. [frameworks](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/p3711.md)
  - 51. [Event orderer and its user interface](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3713.md)
    - 51.1. [Event orderer design philosophy.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3713.md#AEN3728)
    - 51.2. [Using the standard event orderer startup script](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x3733.md)
    - 51.3. [Writing an event orderer startup script](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x3744.md)
    - 51.4. [Event orderer packages](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x3810.md)
  - 52. [Event builder client framework](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3879.md)
    - 52.1. [Application specific code for the event builder](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3879.md#AEN3899)
    - 52.2. [Building event builder clients.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x4067.md)
    - 52.3. [Running event builder clients](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x4112.md)
    - 52.4. [ringFragmentSource - a prepackaged client for ringbuffer data sources](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x4145.md)
  - 53. [Event builder Readout Callouts](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c4231.md)
    - 53.1. [API layer](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c4231.md#AEN4241)
    - 53.2. [EZBuilder](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x4248.md)
  - [Preface](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/f4252.md)
  - [EVBC::start](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r4255.md) -- Start the event builder pipeline.
  - [EVBC::stop](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r4320.md) -- Stop the event builder pipeline.
  - [EVBC::reset](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r4333.md) -- Reset timestamp history
  - [EVBC::flush](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r4347.md) -- Flush event builder event queues.
  - [EVBC::startRingSource](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r4360.md) -- Start a ring fragment source for the event builder.
  - [EVBC::startS800Source](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r4406.md) -- Start S800 data source
  - [Preface](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/f4424.md)
  - [EVBC::initialize](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r4430.md) -- Initialize the EZBuilder layer.
  - [EVBC::onBegin](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r4483.md) -- EZBuilder begin run actions
  - [EVBC::onEnd](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r4502.md) -- EZBuilder end run actions.
  - [Event builder client framework](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r4516.md) -- Event builder cilent framework
  - [EVB::handleFragment](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r4560.md) -- Submit event fragments.
  - [EVB::inputStats](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r4579.md) -- Event builder input statistics
  - [EVB::outputStats](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r4627.md) -- Get orderer output statistics
  - [EVB::dlatestats](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r4646.md) -- Get the late fragment statistics.
  - [EVB::onDataLate](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r4674.md) -- Bind scripts to data late events.
  - [EVB::barriertrace](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r4698.md) -- Supply a script to invoke on barrier events.
  - [EVB::source](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r4718.md) -- Create event source queues.
  - [EVB::deadsource](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r4736.md) -- Mark a data source dead.
  - [EVB::reviveSocket](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r4751.md) -- Revive all dead data sources associated with a socket
  - [EVB::flush](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r4766.md) -- Empty all input queues.
  - [EVB::reset](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r4779.md) -- Reset timestamp clocks.
  - 54. [The SBS Readout framework](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c4792.md)
    - 54.1. [SBS Readout concepts](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c4792.md#AEN4803)
    - 54.2. [Obtaining and building the skeleton application](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5095.md)
    - 54.3. [Modifying the skeleton application to meet your needs](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5110.md)
    - 54.4. [Readout commands](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5182.md)
    - 54.5. [Embedded Tcl server](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5198.md)
    - 54.6. [Running a readout application](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5208.md)
  - 55. [CCUSB Readout framework](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c5213.md)
    - 55.1. [How the CCUSB readout framework works](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c5213.md#AEN5237)
    - 55.2. [Writing DAQ configuration files](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5253.md)
    - 55.3. [Writing device support software](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5294.md)
    - 55.4. [Tcl device driver support](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5455.md)
    - 55.5. [The slow controls subsystem](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5713.md)
    - 55.6. [Running CCUSBReadout](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5726.md)
  - 56. [VMUSB readout](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c5775.md)
    - 56.1. [How the VMUSB readout framework works](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c5775.md#AEN5801)
    - 56.2. [Writing DAQ configuration files](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5817.md)
    - 56.3. [Writing C++ device support software](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5848.md)
    - 56.4. [Writing device support software in Tcl](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x6022.md)
    - 56.5. [The slow controls subsystem](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x6256.md)
    - 56.6. [Pushing external data into the event stream](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x6297.md)
    - 56.7. [Running VMUSBReadout](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x6339.md)
- VII. [Reference Pages](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/p6393.md)
  - I. [1compatibility](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r6395.md)
    - [compatibilitybuffer](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r6397.md) -- Filter ring items to spectrodaq buffers
    - [compatibilitylogger](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r6435.md) -- Create spectrodaq formatted event log files.
    - [eventlog-compat](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r6475.md) -- Provide event logger pipeline for use with ReadoutGUI.
    - [spectcldaq](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r6522.md) -- Pipe data source for SpecTcl in spectrodaq buffer mode.
    - [spectcldaq.server](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r6563.md) -- TCP/IP server of ring data in spectrodaq format.
    - [BufferToRing](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r6624.md) -- Convert old buffered data to ring buffer format.
  - II. [1daq](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r6643.md)
    - [ringbuffer](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r6645.md) -- Manage ring buffers.
    - [ringtostdout](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r6743.md) -- Transmit data from a ring buffer to stdout.
    - [stdintoring](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r6797.md) -- Pipe stdin to a ring buffer.
    - [evttclsh](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r6849.md) -- Tcl interpreter that always runs an event loop
    - [frag2ring](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r6862.md) -- Filter flattened fragments to ring items.
    - [glom](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r6940.md) -- Glue event fragments together into events
    - [S800 Ring fragment data source](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r6979.md) -- Event builder ring fragment source from s800
    - [teering](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r7051.md) -- Tee data to stdout and a ringbuffer.
    - [Readout Gui](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r7076.md) -- Encapsulate data sources in a graphical user interface
    - [evttclsh](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r7696.md) -- Tcl interpreter that always runs an event loop
    - [evttclsh](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r7709.md) -- Tcl interpreter that always runs an event loop
    - [dumper](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r7722.md) -- Produce a formatted dump of event data.
    - [daqstart](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r7798.md) -- Monitor essential programs
    - [eventlog](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r7873.md) -- Record Event Data to Disk.
    - [ringselector](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r7934.md) -- Provide selected ring data to non NSCL DAQ aware clients
    - [sclclient](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r8051.md) -- Maintain scaler state in a tclserver
    - [tkdumper](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r8185.md) -- GUI Dump of ring buffer items.
  - III. [1epics](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r8199.md)
    - [chanlog](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r8201.md) -- Write a set of channels to file
    - [controlpush](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r8257.md) -- 
                Push epics data into a Tcl Server (e.g. production readout).
  - IV. [1evb](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r8356.md)
    - [EVB::BarrierStats::incomplete](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r8358.md) -- Display incomplete barrier statistics
    - [EVB::BarrierStats::queueBarriers](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r8448.md) -- Displays per queue barrier statistics
    - [EVB::BarrierStats::Summary](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r8517.md) -- UI element to summarize barrier statistics.
    - [EVB::CallbackManager](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r8549.md) -- Object that manages callback sets.
    - [EVB::connectionList](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r8629.md) -- List event builder connections
    - [EVB::GUI procs](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r8671.md) -- Standard monitor UI procs.
    - [EVB::inputStatistics::statusDisplay](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r8716.md) -- Widget to display input statitics
    - [EVB::inputStatistics::queueStats](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r8883.md) -- Per queue input statistics widget
    - [::EVB::inputStatistics::queueDisplay](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r8976.md) -- Display input queue statistics
    - [EVB::inputStatistics::summaryDisplay](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r9028.md) -- Summary of input statistics.
    - [EVB::lateFragments](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r9080.md) -- Late fragment statistics
    - [EVB::lateSummary](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r9151.md) -- Widget to display summar of data late fragments.
    - [::EVB::outputStatistics](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r9186.md) -- Complete output statistics widget
    - [::EVB::outputSummary](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r9273.md) -- Summarize output statistics
    - [::EVB::utility::sortedPair](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r9329.md) -- Key value pair widget
    - [::EVB::utility::sortedWidget](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r9424.md) -- General key/widget sorted list
    - [EventBuilder](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r9551.md) -- Event builder utility **proc**s
    - [Observer](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r9685.md) -- Support the Observer pattern
    - [EvbOrderer](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r9784.md) -- Event orderer compiled commands.
  - V. [1tcl](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10013.md)
    - [TCL Ring package.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10015.md) -- Access Rings from tcl.
    - [cratelocator](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10142.md) -- locate specific SBS VME crate controllers.
    - [cesbcnaf](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10168.md) -- CAMAC operation via a CES CAMAC interface
    - [wienerbcnaf](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10193.md) -- CAMAC operation via a Wiener VC32/CC32 board set
    - [bcnaf](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10218.md) -- bcnaf via SBS VME CAMAC interfaces
    - [canev812control](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10254.md) -- GUI for controlling CAEN V812 CFD modules
    - [loadcfd](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10274.md) -- Load settings in to a CAEN V812 CFD module.
    - [loadshaper](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10293.md) -- Load setttings into an N568 shaper via SBS/V288.
    - [n568Control](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10311.md) -- GUI for the n568 shaper.
    - [vhqControl](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10334.md) -- Control panel application for VHQ bias supply modules.
    - [vhsPanel](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10350.md) -- Canned VHS Control panel
    - [SBS Vme Tcl package](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10378.md) -- Provide access to VME crates to Tcl scripts.
    - [DaqPortManager](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10485.md) -- Manage TCP/IP service ports and advertise their allocations
    - [tclserver](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10588.md) -- Start a Tcl Server.
    - [serverauth](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10631.md) -- Control tcl server authorization.
    - [dvdburn](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10677.md) -- Command line tool to burn NSCLDAQ data DVDs.
    - [burngui](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10704.md) -- Graphical front end to dvdburn
    - [ScalerDisplay](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10722.md) -- Live Scaler Displays
  - VI. [1sbsReadout](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10940.md)
    - [Readout](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10942.md) -- Start an event readout program.
  - VII. [3daq](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10982.md)
    - [CopyrightNotice](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10984.md) -- Generate license/author credits.
    - [cvt](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r11080.md) -- Integer byte order conversions
    - [CRingMaster](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r11266.md) -- RingMaster access.
    - [CRingAccess](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r11458.md) -- Remote Ring Access
    - [CRingBuffer](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r11644.md) -- Low level ring buffer primitives
    - [CException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r12452.md) -- Abstract base class for the exception class hierarchy.
    - [CErrnoException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r12539.md) -- Exceptions that wrap the Unix `errno`
    - [CRangeError](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r12616.md) -- Reports and exception for a value out of allowed range.
    - [CStateException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r12754.md) -- Exception for invalid state transitions.
    - [CStreamIOError](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r12853.md) -- I/O error on a C++ stream.
    - [CURIFormatException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r13016.md) -- Report errors in universal resource identifiers (uri)s.
    - [CMonitorException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r13201.md) -- Exceptions for synchronization class abuse.
    - [CInvalidArgumentException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r13336.md) -- Report invalid function arguments.
    - [CDAQShm](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r13470.md) -- class description
    - [CAuthenticator](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r13796.md) -- Abstract base authenticator class.
    - [CPasswordCheck](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r13900.md) -- Authenticate against a stored password.
    - [CUnixUserCheck](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r14088.md) -- Authenticate against a unix user name and password.
    - [CTclAccessListCheck](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r14299.md) -- Authenticate against a Tcl List.
    - [CAccessListCheck](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r14397.md) -- Authenticate against a list of allowed credentials.
    - [CHostListCheck](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r14539.md) -- Authenticate from a list of TCP/IP hosts
    - [CInteractor](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r14719.md) -- Base class for security interactions.
    - [CStringInteractor](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r14888.md) -- Provide an interactor that processes strings.
    - [CFdInteractor](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r15049.md) -- Interact with  file descriptor
    - [CIOInteractor](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r15175.md) -- Separate prompt and input interactors.
    - [CTCLApplication 3](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r15300.md) -- 
                Base class for TCL/Tk applications.
    - [CTCLException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r15343.md) -- 
                Class for reporting exceptional conditions in Tcl applications
                via the C++ try/catch mechanism.
    - [CTCLInterpreter](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r15486.md) -- 
                Encapsulate a Tcl interpreter.
    - [CTCLInterpreterObject  3](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r15704.md) -- 
                Base class for objects that are associated with a Tcl Interpreter.
    - [CTCLList](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r15783.md) -- 
                Provide access to Tcl List parsing.
    - [CTCLObject](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r15892.md) -- 
                Encapsulate Tcl Dual ported objects.
    - [CTCLObjectProcessor](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r16123.md) -- 
                Abstract base class to encapsulate the Tcl object command interface exposed by
                `Tcl_CreateObjCommand`.
    - [CTCLVariable](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r16216.md) -- 
                Encapsulate Tcl interpreter variables.
    - [CTCLProcessor](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r16411.md) -- 
                Provide `argc`, `argv`
                extension commands to Tcl.
    - [CTCLChannel](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r16600.md) -- 
                Provide a C++ abstraction wrapper for Tcl Channels.
    - [CTCLCommandPackage](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r16770.md) -- 
                Group several related Tcl command extensions and common services they
                may require together.
    - [CTCLCompatibiltyProcessor](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r16875.md) -- 
                Adaptor between `CTCLOjbectProcessor`
                and `CTCLProcessor`.
    - [CTCLFileHandler](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r16942.md) -- 
                Base class for building object oriented Tcl File event handlers.
    - [CTCLHashTable](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r17028.md) -- 
                Object oriented interface to Tcl's hash table functions.
    - [CTCLHashTableItem](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r17159.md) -- 
                Encapsulation of an entry in a Tcl Hash table as encapsulated
                in `CTCLHashTable`
    - [CTCLHashTableIterator](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r17227.md) -- 
                Iterator for visiting all elements of a `CTCLHashTable`
    - [CTCLIdleProcess](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r17323.md) -- 
                Allows the establishment of an executable object that
                can be scheduled to be invoked when the Tcl/Tk intperpreter
                has no events that require processing.
    - [CTCLPackagedCommand](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r17384.md) -- 
                Base class for a command that lives in a `CTCLCommandPackage`
    - [CTCLResult](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r17445.md) -- 
                Provide an object oriented interace to the Tcl interpreter result.
    - [CTCLString](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r17556.md) -- 
                Provide a wrapper for the Tcl_DString data type
                and its API
    - [CTCLTimer](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r17773.md) -- 
                Abstract base class for C++ objects attached to timer events.
    - [CTCLLiveEventLoop](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r17843.md) -- Run Tcl with event loop.
    - [CTCLChannelCommander](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r17947.md) -- Accept commands on a Tcl channel from the event loop.
    - [CTCLStdioCommander](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r18159.md) -- Event driven command input on stdin/stdout
    - [CTCLServer](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r18223.md) -- Listener for a Tcl server.
    - [CTCLTcpServerInstance](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r18351.md) -- Channel commander that is a server instance for `CTCLServer`
    - [CTCLObjectPackage](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r18424.md) -- Provide common functionality for a set of
                    related commands.
    - [CTCLPackagedObjectProcessor](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r18486.md) -- Base class for commands living in a
                        `CTCLObjectPackage`
    - [CItemConfiguration](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r18586.md) -- Hold a configuration
    - [CConfigurableObject](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r19309.md) -- Base class for objects tht have a configuration.
    - [Thread](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r19529.md) -- Abstract base class for thread objects.
    - [Synchronizable](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r19663.md) -- Wait queue for threads
    - [SyncGuard](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r19761.md) -- Provide Critical Regions, Monitors
    - [URL](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r19928.md) -- Parse Uniform Resource Identifiers (URI)
    - [CEvbClientApp](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r20076.md) -- Framework event builder client application.
    - [CEVBClientFramework](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r20220.md) -- Event builder client framework.
    - [CEventOrderClient](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r20276.md) -- Client of the event orderer
    - [CRingItem](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r20487.md) -- Encapsulates an item in a ring buffer.
    - [CRingScalerItem](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r20784.md) -- Encapsulate ring buffer scaler items.
    - [CRingStateChangeItem](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r21133.md) -- Encapsulate a ring buffer state change item.
    - [CRingTextItem](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r21444.md) -- Encapsulate ring items that are lists of text strings.
    - [CRingPhysicsEventCountItem](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r21671.md) -- Provides statistics regarding the number of events produced.
    - [CRingFragmentItem](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r21906.md) -- Encapsulate a EVB_FRAGMENT ring item
    - [CRingSelectionPredicate](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r22179.md) -- Base class for predicates that select items from
                ring buffers.
    - [CAllButPredicate](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r22510.md) -- Select all ring items except some.
    - [CDesiredTypesPredicate](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r22685.md) -- Only accept specified ring item types.
    - [DataFormat.h](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r22849.md) -- Format of ring items.
    - [format  Functions](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r23303.md) -- Functions to create ring items.
    - [CDataSource](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r23559.md) -- Abstract base class of data source for ring items.
    - [CRingDataSource](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r23600.md) -- Ringbuffer data source for ring items.
    - [CFileDataSource](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r23668.md) -- Ring item data source from a file
    - [CDataSourceFactory"](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r23725.md) -- Create data sources given a URI
    - [CRingItemFactory](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r23781.md) -- Upcast ring items to specific ring item objects.
    - [CException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r23873.md) -- Abstract base class for the exception class hierarchy.
    - [CErrnoException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r23960.md) -- Exceptions that wrap the Unix `errno`
    - [CRangeError](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r24037.md) -- Reports and exception for a value out of allowed range.
    - [CStateException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r24175.md) -- Exception for invalid state transitions.
    - [CStreamIOError](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r24274.md) -- I/O error on a C++ stream.
    - [CURIFormatException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r24437.md) -- Report errors in universal resource identifiers (uri)s.
    - [CMonitorException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r24622.md) -- Exceptions for synchronization class abuse.
    - [CInvalidArgumentException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r24757.md) -- Report invalid function arguments.
    - [CTCLApplication 3](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r24891.md) -- 
                Base class for TCL/Tk applications.
    - [CTCLException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r24934.md) -- 
                Class for reporting exceptional conditions in Tcl applications
                via the C++ try/catch mechanism.
    - [CTCLInterpreter](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r25077.md) -- 
                Encapsulate a Tcl interpreter.
    - [CTCLInterpreterObject  3](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r25295.md) -- 
                Base class for objects that are associated with a Tcl Interpreter.
    - [CTCLList](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r25374.md) -- 
                Provide access to Tcl List parsing.
    - [CTCLObject](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r25483.md) -- 
                Encapsulate Tcl Dual ported objects.
    - [CTCLObjectProcessor](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r25714.md) -- 
                Abstract base class to encapsulate the Tcl object command interface exposed by
                `Tcl_CreateObjCommand`.
    - [CTCLVariable](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r25807.md) -- 
                Encapsulate Tcl interpreter variables.
    - [CTCLProcessor](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r26002.md) -- 
                Provide `argc`, `argv`
                extension commands to Tcl.
    - [CTCLChannel](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r26191.md) -- 
                Provide a C++ abstraction wrapper for Tcl Channels.
    - [CTCLCommandPackage](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r26361.md) -- 
                Group several related Tcl command extensions and common services they
                may require together.
    - [CTCLCompatibiltyProcessor](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r26466.md) -- 
                Adaptor between `CTCLOjbectProcessor`
                and `CTCLProcessor`.
    - [CTCLFileHandler](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r26533.md) -- 
                Base class for building object oriented Tcl File event handlers.
    - [CTCLHashTable](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r26619.md) -- 
                Object oriented interface to Tcl's hash table functions.
    - [CTCLHashTableItem](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r26750.md) -- 
                Encapsulation of an entry in a Tcl Hash table as encapsulated
                in `CTCLHashTable`
    - [CTCLHashTableIterator](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r26818.md) -- 
                Iterator for visiting all elements of a `CTCLHashTable`
    - [CTCLIdleProcess](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r26914.md) -- 
                Allows the establishment of an executable object that
                can be scheduled to be invoked when the Tcl/Tk intperpreter
                has no events that require processing.
    - [CTCLPackagedCommand](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r26975.md) -- 
                Base class for a command that lives in a `CTCLCommandPackage`
    - [CTCLResult](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r27036.md) -- 
                Provide an object oriented interace to the Tcl interpreter result.
    - [CTCLString](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r27147.md) -- 
                Provide a wrapper for the Tcl_DString data type
                and its API
    - [CTCLTimer](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r27364.md) -- 
                Abstract base class for C++ objects attached to timer events.
    - [CTCLLiveEventLoop](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r27434.md) -- Run Tcl with event loop.
    - [CTCLChannelCommander](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r27538.md) -- Accept commands on a Tcl channel from the event loop.
    - [CTCLStdioCommander](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r27750.md) -- Event driven command input on stdin/stdout
    - [CTCLServer](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r27814.md) -- Listener for a Tcl server.
    - [CTCLTcpServerInstance](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r27942.md) -- Channel commander that is a server instance for `CTCLServer`
    - [CTCLObjectPackage](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r28015.md) -- Provide common functionality for a set of
                    related commands.
    - [CTCLPackagedObjectProcessor](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r28077.md) -- Base class for commands living in a
                        `CTCLObjectPackage`
    - [CItemConfiguration](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r28177.md) -- Hold a configuration
    - [CConfigurableObject](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r28900.md) -- Base class for objects tht have a configuration.
    - [CException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r29120.md) -- Abstract base class for the exception class hierarchy.
    - [CErrnoException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r29207.md) -- Exceptions that wrap the Unix `errno`
    - [CRangeError](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r29284.md) -- Reports and exception for a value out of allowed range.
    - [CStateException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r29422.md) -- Exception for invalid state transitions.
    - [CStreamIOError](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r29521.md) -- I/O error on a C++ stream.
    - [CURIFormatException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r29684.md) -- Report errors in universal resource identifiers (uri)s.
    - [CMonitorException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r29869.md) -- Exceptions for synchronization class abuse.
    - [CInvalidArgumentException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r30004.md) -- Report invalid function arguments.
    - [CTCLApplication 3](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r30138.md) -- 
                Base class for TCL/Tk applications.
    - [CTCLException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r30181.md) -- 
                Class for reporting exceptional conditions in Tcl applications
                via the C++ try/catch mechanism.
    - [CTCLInterpreter](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r30324.md) -- 
                Encapsulate a Tcl interpreter.
    - [CTCLInterpreterObject  3](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r30542.md) -- 
                Base class for objects that are associated with a Tcl Interpreter.
    - [CTCLList](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r30621.md) -- 
                Provide access to Tcl List parsing.
    - [CTCLObject](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r30730.md) -- 
                Encapsulate Tcl Dual ported objects.
    - [CTCLObjectProcessor](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r30961.md) -- 
                Abstract base class to encapsulate the Tcl object command interface exposed by
                `Tcl_CreateObjCommand`.
    - [CTCLVariable](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r31054.md) -- 
                Encapsulate Tcl interpreter variables.
    - [CTCLProcessor](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r31249.md) -- 
                Provide `argc`, `argv`
                extension commands to Tcl.
    - [CTCLChannel](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r31438.md) -- 
                Provide a C++ abstraction wrapper for Tcl Channels.
    - [CTCLCommandPackage](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r31608.md) -- 
                Group several related Tcl command extensions and common services they
                may require together.
    - [CTCLCompatibiltyProcessor](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r31713.md) -- 
                Adaptor between `CTCLOjbectProcessor`
                and `CTCLProcessor`.
    - [CTCLFileHandler](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r31780.md) -- 
                Base class for building object oriented Tcl File event handlers.
    - [CTCLHashTable](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r31866.md) -- 
                Object oriented interface to Tcl's hash table functions.
    - [CTCLHashTableItem](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r31997.md) -- 
                Encapsulation of an entry in a Tcl Hash table as encapsulated
                in `CTCLHashTable`
    - [CTCLHashTableIterator](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r32065.md) -- 
                Iterator for visiting all elements of a `CTCLHashTable`
    - [CTCLIdleProcess](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r32161.md) -- 
                Allows the establishment of an executable object that
                can be scheduled to be invoked when the Tcl/Tk intperpreter
                has no events that require processing.
    - [CTCLPackagedCommand](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r32222.md) -- 
                Base class for a command that lives in a `CTCLCommandPackage`
    - [CTCLResult](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r32283.md) -- 
                Provide an object oriented interace to the Tcl interpreter result.
    - [CTCLString](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r32394.md) -- 
                Provide a wrapper for the Tcl_DString data type
                and its API
    - [CTCLTimer](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r32611.md) -- 
                Abstract base class for C++ objects attached to timer events.
    - [CTCLLiveEventLoop](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r32681.md) -- Run Tcl with event loop.
    - [CTCLChannelCommander](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r32785.md) -- Accept commands on a Tcl channel from the event loop.
    - [CTCLStdioCommander](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r32997.md) -- Event driven command input on stdin/stdout
    - [CTCLServer](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r33061.md) -- Listener for a Tcl server.
    - [CTCLTcpServerInstance](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r33189.md) -- Channel commander that is a server instance for `CTCLServer`
    - [CTCLObjectPackage](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r33262.md) -- Provide common functionality for a set of
                    related commands.
    - [CTCLPackagedObjectProcessor](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r33324.md) -- Base class for commands living in a
                        `CTCLObjectPackage`
    - [CItemConfiguration](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r33424.md) -- Hold a configuration
    - [CConfigurableObject](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r34147.md) -- Base class for objects tht have a configuration.
    - [CVMEInterface](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r34367.md) -- Class wrapping of the SBS VME library.
    - [CSBSBit3VmeInterface](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r34682.md) -- Provide access to SBS/Bit3 driver parameters.
    - [CVME<T>](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r35231.md) -- Reference counted pointer like object to VME address segments.
    - [CVMEModule](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r35632.md) -- Provide a base set of services for a VME module driver class.
    - [CMmapError](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r35957.md) -- Report errors in memory mapping requests.
    - [CADC2530](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r36013.md) -- Support the Hytec NADC 2530 Peak sensing ADC.
    - [CAENcard](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r36475.md) -- Support for the CAEN 32 bit digitizers
    - [CBD8210](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r37270.md) -- CES CBD 8210 CAMAC branch highway driver (obsolete)
    - [CCAENV1x90](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r37638.md) -- Support for the CAEN V1190 and V1290
                        multihit, complicated TDC.
    - [CCAENV560](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r40020.md) -- Support the CCAENV560 non-latching scaler.
    - [CCAENV830](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r40184.md) -- Support driver for the CAEN V820/V830 latching scaler module.
    - [CCAENV977](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r40741.md) -- Software support for the CAEN V977 I/O register.
    - [CCAMACScalerLRS2551](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r41140.md) -- Support software for the LeCroy LRS 2551 12 channel CAMAC scaler
    - [CCAMACScalerLRS4434](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r41250.md) -- High level support software for the 32 channel LeCroy LRS 4434 CAMAC scaler module
    - [CCAMACStatusModule](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r41362.md) -- Provide computer busy status support for the BiRA CAMAC
                    NIM out module.
    - [CCAMACTrigger](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r41470.md) -- Trigger module for the CES CBD 8210 VME CAMAC Parallel Branch Highway Driver
    - [CCamac](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r41524.md) -- Manages CAMAC memory maps.
    - [CCamacModule](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r41606.md) -- Provide support for a generic CAMAC module.
    - [CCamacNimout](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r41980.md) -- Provides low level support for the BiRa CAMAC Nim output module.
    - [CCrateController](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r42069.md) -- Encapsulation of a BiRa 1302 CAMAC controller via CES CBS8210.
    - [CSIS3600](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r42409.md) -- Support for the SIS 3600 VME latch module.
    - [CSIS3820](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r42868.md) -- Low level support for SIS 3820 32 channel latching scaler module
    - [CScaler](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r43574.md) -- Abstract base class for reading scalers into a vector
    - [CStatusModule](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r43681.md) -- Abstract base class for status modules.
    - [CTrigger](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r43746.md) -- Abstract base class for triggers
    - [CVME](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r43774.md) -- Pointer like object for accessing the VME
    - [CVMEScalerLRS1151](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r44118.md) -- High level support for the LeCroy LRS 1151 VME scaler.
    - [CVMEStatusModule](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r44205.md) -- Implement a status module using the CAEN V262 module.
    - [CVMETrigger](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r44289.md) -- VME trigger class based on the CAEN V262 I/O module.
    - [CVMEptr](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r44340.md) --
    - [CaenIO](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r44683.md) -- Support for the CAEN V262 I/O register module.
    - [CMmapError](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r44830.md) -- Exception that can be thrown in the event of memory mapping errors.
    - [CNimout](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r44865.md) -- Low level support for the BiRa VME nim output module
    - [CVmeModule](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r45139.md) -- Convenience base class for implementing VME module support
    - [CSIS3300](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r45437.md) -- Low Level support for the SIS 3300 Flash ADC module
    - [CPortManager](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r46170.md) -- Provide a C++ interface to the server port manager daemon.
    - [CPortManagerException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r46317.md) -- Report errors conditions in port manager transactions
  - VIII. [3ccusb](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r46463.md)
    - [addtcldriver](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r46465.md) -- Register Tcl command ensemble as a device module
    - [ad811](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r46491.md) -- Support the Ortec AD811 ADC
    - [c1205](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r46547.md) -- Manage CAEN C1205 QDC modules.
    - [c257](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r46667.md) -- Manages the C257 scaler module
    - [ccusb (command)](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r46740.md) -- Configure and read scalers from CC-USB module
    - [lrs2228](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r46940.md) -- Manages the LRS2228 TDC
    - [lrs2249](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r46997.md) -- Manage LeCroy 2249 QDC modules
    - [lrs2551](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r47050.md) -- Manage LRS 2551 modules
    - [ph7xxx](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r47126.md) -- Define Phillips ADC/TDC/QDC modules
    - [stack](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r47320.md) -- Create and configure CC-USB stacks.
    - [Module](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r47448.md) -- Create and manipulate slow control device instances
    - [Slow controls protocol](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r47490.md) -- TCP/IP slow control protocol
    - [CCCUSB](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r47601.md) -- Provide access to a CC-USB device.
    - [CCCUSBReadoutList](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r50336.md) -- Create lists of CAMAC commands for CC-USB controllers.
    - [CConfigurableObject](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r50799.md) -- base class for devices that have a configuration
    - [cccusb](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r52051.md) -- Swig wrapping of the CCCUSB C++ class.
    - [cccusbreadoutlist](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r52779.md) -- Tcl wrapping of `CCCUSBReadoutList`
  - IX. [3vmusb](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r53046.md)
    - [adc](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r53048.md) -- Create/configure CAEN V775, V785, V792, V862 modules.
    - [caenchain](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r53182.md) -- Aggregate adc modules into CBLT readout chains.
    - [vmusb](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r53231.md) -- Control VM-USB resources and read internal scalers
    - [sis330x](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r53428.md) -- Driver for SIS3300/1 FADC
    - [sis3820](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r53592.md) -- Create and configure SIS 3820 scaler modules
    - [v830](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r53638.md) -- Create and configure CAEN V830 32 channel scalers.
    - [v977](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r53817.md) -- Create and configure CAEN V977 Input registers
    - [sis3804](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r53929.md) -- Create and configure SIS 3804 scalers
    - [hinp](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r53988.md) -- XLM-XXV with Wash-U HINP firmware.
    - [psd](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r54047.md) -- XLM with Wash-U pulse shape discrmination firmware
    - [hira](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r54082.md) -- Pair up to 2 XLMs and FADC for HiRA
    - [hytec](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r54134.md) -- Support the Hytec NADC 2530 adc module.
    - [tcl driver support](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r54289.md) -- tcl driver support functions.
    - [madc](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r54426.md) -- Acquire events from Mesytec MADC32 ADC.
    - [madcchain](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r54677.md) -- Support CBLT chains of MADC32 modules.
    - [madcscaler](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r54738.md) -- Support dead-time counters in MADC32 as scalers.
    - [mase](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r54775.md) -- Support for XLM with MASE firmware.
    - [tdc1x90](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r54825.md) -- Provide support for the CAEN V1x90 TDC family.
    - [v1729a](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r55080.md) -- CAENV1729a waveform digitizer.
    - [stack](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r55210.md) -- Compose and configure VM-USB readout stacks.
    - [CVMUSB](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r55338.md) -- Interface with VM-USB controller.
    - [CVMUSBReadoutList](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r57342.md) -- Construct VM-USB stacks
    - [CVMUSBRemote](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r58237.md) -- Execute lists remotely on VMUSBReadout
    - [CConfigurableObject](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r59464.md) -- Configuration database
    - [cvmusb](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r60631.md) -- SWIG Tcl wrapping of `CVMUSB`
    - [cvmusbreadoutlist](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r61379.md) -- SWIG wrappers for `CVMUSBReadoutList`
    - [Module](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r61869.md) -- control config command: create/configure modules.
    - [watch](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r62123.md) -- Watch variables (slow controls)
    - [VMUSB slow controls protocol](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r62142.md) -- VMUSB Slow controls protocol
  - X. [3tcl](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r62204.md)
    - [s800](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r62206.md) -- s800 Readout Callouts module
    - [caennet](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r62291.md) -- Access CAENnet from Tcl scripts.
    - [camac](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r62356.md) -- Provide access to CES CBD8210 CAMAC to Tcl scripts
    - [wienercamac](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r62523.md) -- Tcl Script CAMAC access via VC32/CC32 boardset.
    - [CFD812](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r62661.md) -- low level control of the CAEN V812 CFD
    - [caenv812gui](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r62801.md) -- Megawidget control panel for the CAEN V812 CFD
    - [n568b](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r62933.md) -- Support package for the CAEN N568B shaper.
    - [n568Panel](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r63121.md) -- Control panel megawidget for N568 shaping amplifier
    - [vhq](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r63258.md) -- Low level Tcl access to iSEG VHQ2xxx units.
    - [vhqPanel](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r63445.md) -- Control widget for iSeg vhq2xx VME bias supply.
    - [iSegVhs](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r63638.md) -- SBS support for VHS 404 modules.
    - [VhsWidgets](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r64142.md) -- User interface components for VHS 404 power supplies.
    - [portAllocator](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r64221.md) -- Tcl API for the DaqPortManager daemon.
    - [DvdBurner](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r64299.md) -- Burn NSCL Data to DVD
    - [sequencer](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r64351.md) -- 
                Provide a ReadoutGui plugin for nscldaq 8.1 and later that can
                automate several data taking runs.
  - XI. [3sbsReadout](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r64477.md)
    - [CBusy](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r64479.md) -- Abstract base class for Busy module management.
    - [CCAENV262Busy](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r64534.md) -- Concrete busy class for the CAEN V262 input module.
    - [CCAENV262Triger](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r64659.md) -- Trigger module with CAEN V262
    - [CCompoundEventSegment](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r64763.md) -- Container for other event segments
    - [CDocumentedPacket](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r64985.md) -- Encapsulate event data in a packet that is documented.
    - [CEventPacket](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r65248.md) -- Encapsulate an event segment in a documented packet.
    - [CEventSegment](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r65366.md) -- Base class for all event segments.
    - [CEventTrigger](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r65545.md) -- Abstract base class for triggers.
    - [CExperiment](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r65600.md) -- Encapsulate the experiment.
    - [CInvalidPacketStateException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r65873.md) -- Exception thrown by documented packets.
    - [CNullTrigger](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r65983.md) -- A trigger that never fires.
    - [CReadoutException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r66003.md) -- Base class for readout specific exceptions
    - [CScalerBank](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r66027.md) -- Container for individual Scaler objects.
    - [CTimedTrigger](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r66269.md) -- CEventTrigger that fires periodically
    - [CV977Busy](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r66357.md) -- Concrete busy class using the CAEN V977 module
    - [CV977Trigger](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r66459.md) -- Concrete Trigger class using CAEN V977 module.
    - [RunState](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r66553.md) -- Encapsulate important state of the software.
    - [CScaler](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r66653.md) -- Base class for scaler readout classes
  - XII. [5daq](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r66739.md)
    - [eventorderer](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r66741.md) -- Event orderer protocol
  - XIII. [5tcl](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r66856.md)
    - [caen812configfile](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r66858.md) -- Format of configuration files for CAENV 812 software.
    - [n568configfile](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r66964.md) -- N568 shaper configuration file
    - [vhqconfig](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r67080.md) --  Config file for

- **List of Tables**
- 7-1. [Data Acquisition configuration parameters](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x513.md#AEN575)
- 7-2. [Directory root configuration parameters](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x513.md#AEN596)
- 7-3. [State Parameters](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x513.md#AEN616)
- 47-1. [Wiener CC32 addressing convention](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x3388.md#AEN3392)

- **List of Figures**
- 7-1. [Readout GUI Directory tree](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x479.md#AEN495)

- **List of Examples**
- 2-1. [Adding **ringbuffer**'s directory to bash's search path:](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c265.md#AEN278)
- 2-2. [Adding command paths to csh](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c265.md#AEN284)
- 5-1. [Appending the NSCLDAQ Tcl Package repository to Tcl's search
            path](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c342.md#AEN366)
- 5-2. [Appending NSLCDAQ's TclPackage repository to Tcl's search path](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c342.md#AEN370)
- 5-3. [Requesting the VME Tcl package be loaded.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c342.md#AEN374)
- 5-4. [Using VME Tcl to locate all 2530 modules](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x377.md#AEN381)
- 7-1. [ReadoutCallouts.tcl sample extension](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x513.md#AEN561)
- 15-1. [Using **serverauth** to authorize a node](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c926.md#AEN941)
- 16-1. [Dumping data from the ring buffer named 0400x on spdaq22](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c945.md#AEN959)
- 16-2. [Dumping data from the event file segment
            /user/0400x/complete/run-1234-00.evt](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c945.md#AEN963)
- 16-3. [State Transition items](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c945.md#AEN976)
- 16-4. [Text List items](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c945.md#AEN981)
- 16-5. [Incremental Scalers dump](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c945.md#AEN986)
- 16-6. [Event count items](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c945.md#AEN992)
- 16-7. [Physics Event items](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c945.md#AEN998)
- 16-8. [Unknown item types](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c945.md#AEN1003)
- 17-1. [Converting a ring buffer event file with compatibilitybuffer](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1009.md#compatibilitybuffer-ex1)
- 17-2. [Converting ring buffer data to a 8Kword (16Kbyte) old style event file](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1009.md#AEN1030)
- 17-3. [Using compatibilitylogger to convert event files](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x1046.md#AEN1060)
- 17-4. [Attaching SpecTcl to ring buffers in compatibility mode](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x1065.md#AEN1080)
- 18-1. [Logging errors and informing on exit](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1105.md#AEN1122)
- 19-1. [Requesting the DvdBurner package](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1128.md#AEN1137)
- 19-2. [Writing runs to DVD using DvdBurner](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1128.md#AEN1143)
- 19-3. [Writing all runs to DVD](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1128.md#AEN1149)
- 21-1. [Taking data from a remote ring](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1164.md#AEN1189)
- 22-1. [Dumping state changes and sampled event data with od](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1194.md#AEN1247)
- 22-2. [Dumping all but packet types](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1194.md#AEN1255)
- 22-3. [Attaching SpecTcl](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1194.md#AEN1263)
- 25-1. [Loading the sequencer package](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1299.md#AEN1349)
- 26-1. [Including the cvt header](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1391.md#AEN1401)
- 26-2. [Compiling a C or C++ source file that includes cvt.h](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1391.md#AEN1407)
- 26-3. [A makefile rule that builds a C++ program using the
                cvt package](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1391.md#AEN1411)
- 26-4. [Creating a DaqConversion](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x1415.md#AEN1428)
- 27-1. [Including the header](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1472.md#AEN1481)
- 27-2. [Compiling code](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1472.md#AEN1484)
- 27-3. [Linking code to the library](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1472.md#AEN1487)
- 28-1. [A sample ring specification in URI form](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1492.md#AEN1500)
- 28-2. [Substituting local host for the hostname in URI's](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1492.md#AEN1508)
- 28-3. [Including the header](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1492.md#AEN1540)
- 28-4. [Compiling code that uses `CRingAccess`](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1492.md#AEN1543)
- 28-5. [Linking code that uses `CRingAccess`](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1492.md#AEN1547)
- 29-1. [Compilation line for ring buffer primitives](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1553.md#AEN1574)
- 29-2. [Including the ring buffer primitives header](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1553.md#AEN1580)
- 29-3. [Linking to the ring buffer primitives](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1553.md#AEN1586)
- 29-4. [Sample ring buffer consumer](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x1590.md#AEN1604)
- 29-5. [A sample Ring Buffer producer program](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x1590.md#AEN1653)
- 30-1. [Incorporating the ring package in your scripts](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1673.md#AEN1680)
- 31-1. [Catching `CException` and exiting](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x1719.md#AEN1744)
- 32-1. [Shared memory library example](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1749.md#AEN1790)
- 32-2. [Compiling a C++ source that includes daqshm.h](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x1820.md#AEN1831)
- 32-3. [Linking C++ object files that use the
            daqshm library](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x1820.md#AEN1835)
- 33-1. [Compilation switches for the security includes](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1839.md#AEN1852)
- 33-2. [Link switches for the security library](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c1839.md#AEN1856)
- 33-3. [Boilerplate DAQ Authorization code](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x1859.md#AEN1863)
- 35-1. [The life of a thread](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c2030.md#AEN2053)
- 35-2. [Why synchonization is needed](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c2030.md#AEN2085)
- 35-3. [Using `SyncGuard` to implement a monitor](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c2030.md#AEN2109)
- 35-4. [Compiling and linking NSCLDAQ threaded software](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2131.md#AEN2139)
- 36-1. [Sample URI library program](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c2159.md#AEN2187)
- 36-2. [Building urltst.cpp](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c2159.md#AEN2213)
- 37-1. [Connecting to the event builder as a data source.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2264.md#AEN2267)
- 37-2. [Closing an event builder connection](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2297.md#AEN2312)
- 37-3. [Starting the event builder](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2405.md#AEN2416)
- 37-4. [Establishing the connection callback](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2439.md#AEN2447)
- 37-5. [Setting up the disconnect callback](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2439.md#AEN2464)
- 38-1. [Including a ring item class](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2744.md#AEN2750)
- 38-2. [Telling the compiler where to find Ring Item headers](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2744.md#AEN2757)
- 38-3. [Linking the ring item format libraries](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2744.md#AEN2762)
- 39-1. [A ReadoutCallouts.tcl for the s800](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2888.md#AEN2905)
- 40-1. [Catching `CException` and exiting](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x2960.md#AEN2985)
- 42-1. [Catching `CException` and exiting](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x3079.md#AEN3104)
- 47-1. [Enabling a module Lam with wienercamac](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x3388.md#AEN3526)
- 49-1. [The CONNECT message format](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3544.md#AEN3579)
- 49-2. [Format of the DISCONNECT message](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3544.md#AEN3594)
- 49-3. [Format of the LIST command](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3544.md#AEN3608)
- 49-4. [Format of the REGISTER command](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3544.md#AEN3660)
- 49-5. [Format of the UNREGISTER message](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3544.md#AEN3670)
- 49-6. [Format of the REMOTE message](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3544.md#AEN3681)
- 51-1. [The standard startup script explained](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x3744.md#AEN3749)
- 52-1. [`CEVBClientApp` definition](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3879.md#AEN3925)
- 52-2. [The `CEVBRingClientApp` class
                definition.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3879.md#AEN3957)
- 52-3. [The `CEVBRingClientApp` `initialize`
                and `shutdown` methods.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3879.md#AEN3971)
- 52-4. [The `CEVBRingClientApp`
`dataReady` method.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3879.md#AEN3984)
- 52-5. [The `EVBRingClientApp` `getEvents`
                implementation.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/c3879.md#AEN4028)
- 52-6. [Configuring the event builder client framework](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x4067.md#AEN4078)
- 52-7. [S800 timestamp extractor (s800timestamp.c](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x4145.md#AEN4184)
- 54-1. [Obtaining the SBS readout skeleton](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5095.md#AEN5100)
- 55-1. [Creating and configuring devices](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5253.md#AEN5257)
- 55-2. [Configuring an event stack](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5253.md#AEN5280)
- 55-3. [Setting up a scaler stack](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5253.md#AEN5291)
- 55-4. [Obtaining the ccusb driver development kit](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5294.md#AEN5299)
- 55-5. [Using a user written CCUSB driver](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5294.md#AEN5305)
- 55-6. [A snit CCUSB device driver module](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5455.md#AEN5502)
- 55-7. [CCUSB device support example writtin in Incr Tcl](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5455.md#AEN5599)
- 55-8. [DAQ config script fragment with tcl drivers.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5455.md#AEN5710)
- 56-1. [Creating and configuring devices](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5817.md#AEN5821)
- 56-2. [Configuring an event stack](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5817.md#AEN5833)
- 56-3. [Configuring a VM-USB scaler stack](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5817.md#AEN5842)
- 56-4. [Obtaning the VM-USB device driver development kit](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5848.md#AEN5856)
- 56-5. [Using a user written VMUSB driver](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5848.md#AEN5865)
- 56-6. [The template driver `Initialize` method](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5848.md#AEN5927)
- 56-7. [Template Driver `addReadoutList` method](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5848.md#AEN5946)
- 56-8. [The VMUSB driver `Xxxx_Init`
                    function.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x5848.md#AEN5972)
- 56-9. [Itcl VM-USB device driver](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x6022.md#AEN6045)
- 56-10. [A Snit VM-USB driver.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x6022.md#AEN6137)
- 56-11. [USing a Tcl VM-USB driver.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x6022.md#AEN6242)
- 56-12. [Specifying VM-USB monitored variables](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/x6297.md#AEN6321)
- 1. [Attaching SpecTcl to a ring buffer in compatibility mode](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r6522.md#AEN6554)
- 1. [Running spectcldaq.server](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r6563.md#AEN6616)
- 2. [Connecting to spectcldaq.server](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r6563.md#AEN6621)
- 1. [Sample output from **ringbuffer status**](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r6645.md#AEN6715)
- 1. [making hex dumps of data from a ring buffer.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r6743.md#AEN6794)
- 1. [Using stdintoring](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r6797.md#AEN6846)
- 1. [Logging extension to readout gui](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r7076.md#AEN7693)
- 1. [Dumping state changes and sampled event data with od](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r7934.md#AEN8031)
- 2. [Dumping all but packet types](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r7934.md#AEN8039)
- 3. [Attaching SpecTcl](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r7934.md#AEN8047)
- 1. [Starting sclclient](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r8051.md#AEN8177)
- 1. [Viewing a set of channel values interactively](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r8201.md#AEN8235)
- 2. [Writing a set of channels to a file](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r8201.md#AEN8238)
- 3. [Appending a set of channels to a file](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r8201.md#AEN8241)
- 4. [Piping a set of channels to a program for processing](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r8201.md#AEN8244)
- 1. [Supporting an observer in a snit type or widget](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r9685.md#AEN9766)
- 2. [Supporting multiple observers in a snit type or widget](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r9685.md#AEN9777)
- 1. [Creating a coypright notice on stderr](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10984.md#AEN11073)
- 2. [Creating an author credit on stderr](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r10984.md#AEN11077)
- 1. [Using `CRingAccess` to connect to
                    a local ring.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r11458.md#AEN11636)
- 2. [Using `CRingAccess` to connect to a remote
                ring](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r11458.md#AEN11640)
- 1. [Message filter predicate](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r11644.md#AEN12397)
- 1. [Calling `CStringInteractor` specific
         members](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r14888.md#AEN15045)
- 1. [evttclsh](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r17843.md#AEN17944)
- 1. [Selecting sampled event from a ring.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r20487.md#AEN20756)
- 1. [Constructing a scaler item from an item gotten from a ring](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r20784.md#AEN21108)
- 1. [Creating a begin run state transition item](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r21133.md#AEN21441)
- 1. [evttclsh](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r27434.md#AEN27535)
- 1. [evttclsh](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r32681.md#AEN32782)
- 1. [Creating a CAENcard geographically](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r36475.md#AEN37254)
- 2. [Setting a TDC to common stop mode](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r36475.md#AEN37258)
- 3. [Reading out a CAEN 785 e.g.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r36475.md#AEN37262)
- 1. [Initializing branch 0](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r37270.md#AEN37631)
- 1. [Using the LRS 1151 in the production readout framework.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r44118.md#AEN44202)
- 1. [Creating a device driver via private derivation](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r45139.md#AEN45256)
- 2. [Creating a device driver via inclusion](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r45139.md#AEN45262)
- 1. [Allocating a port with the port manager](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r46170.md#AEN46304)
- 2. [Listing the port allocatiosn on a system.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r46170.md#AEN46308)
- 1. [Catching a CPortManagerException](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r46317.md#AEN46453)
- 1. [AD811 configuration file example](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r46491.md#AEN46544)
- 1. [LRS2228 creation example](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r46940.md#AEN46994)
- 1. [The lrs2551 command](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r47050.md#AEN47123)
- 1. [Using the **list** command to
                                  construct pedestals](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r47126.md#AEN47226)
- 2. [Sample **ph7xxx** commands](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r47126.md#AEN47316)
- 1. [Example of the **stack** command.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r47320.md#AEN47427)
- 1. [Listing CC-USB Serial numbers (Tcl).](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r52051.md#AEN52714)
- 2. [Creating a CCCUSB object by serial number (Tcl).](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r52051.md#AEN52724)
- 1. [Sample ADC commands](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r53048.md#AEN53175)
- 1. [Using the **caenchain** command.](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r53182.md#AEN53227)
- 1. [Configuring an SIS3820 scaler module](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r53592.md#AEN53635)
- 1. [Configuring a CAEN V830 scaler](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r53638.md#AEN53814)
- 1. [Configuring the SIS 3804 scaler](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r53929.md#AEN53985)
- 1. [Sample Hytec 2530 configuration](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r54134.md#AEN54265)
- 1. [Sample use of madc command](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r54426.md#AEN54656)
- 1. [Building Stacks](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r55210.md#AEN55335)
- 1. [Hooking update methods to recurring timer](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r64142.md#AEN64213)
- 1. [Allocating a service port in Tcl](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r64221.md#AEN64286)
- 2. [Listing allocated ports in Tcl](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r64221.md#AEN64290)
- 1. [Action script example](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r64351.md#AEN64465)
- 2. [Sequencer column configuration file](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r64351.md#AEN64471)
- 1. [Creating and registering a V262 as a busy:](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r64534.md#AEN64650)
- 1. [Deep iteration of `CCompondEventSegment` elements](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r64763.md#AEN64973)
- 2. [Deep visitation of `CCompoundEventSegment` elements](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r64763.md#AEN64977)
- 1. [Using the `CDocumentedPacket` class](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r64985.md#AEN65240)
- 1. [Catching readout specific examples](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r66003.md#AEN66020)
- 1. [Deep visitation in `CScalerBank` containers](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r66027.md#AEN66261)
- 1. [Outputting the state of the run](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r66553.md#AEN66650)
- 1. [Sample configuration file](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r66858.md#AEN66956)
- 1. [Sample configuration file](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r66964.md#AEN67072)
- 1. [Sample configuration file](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/r67080.md#AEN67088)

---

---

[← Preface](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/f4424.md) | [Home](https://github.com/FRIBDAQ/docs/tree/main/Home.md) | [libraries →](https://github.com/FRIBDAQ/docs/tree/main/10.2-106/p1389.md)
