|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="vmusb3-CVMUSBRemote"></a>CVMUSBRemote

<a name="AEN93524"></a>## Name

CVMUSBRemote -- Execute lists remotely on VMUSBReadout

<a name="AEN93527"></a>## Synopsis

```
CVMUSBRemote
```

<a name="AEN94713"></a>## DESCRIPTION

Provides remote access to the VM-USB via the VMUSBReadout's
            slow controls server.  This class is a proxy and transparently
            performs network operations with the slow control server to
            execute each method.

<a name="AEN94716"></a>## METHODS

With the exception of the constructor, please refer to
            [[r90603]]
            for per method documentation.
            The constructor forms a connection with the VMUSBReadout's
            control server or throws an exception if that is not possible.

The parameter constrcutors are:



` std::string deviceName = "vmusb";`The n ame of the device driver to direct requests to.
                        This is the name of the driver instance
                        created by the **Module** command
                        in the control configuration file.

` std::string host = "localhost";`The host in which the readout software is running.

` unsigned int port = 27000;`The port on which the control server is running.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CVMUSBReadoutList | Up | CConfigurableObject |
