|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 67. TCPIP classes | Next |


---

# <a name="AEN15811"></a>67.2. Incorporating the socket library

Using one of the TCP/IP library classes requires that you #include
            the appropriate header.   Doing this requires that you allow the
            C++ compiler to search the DAQ includes directory.  This is most
            simply done by:



1. Sourcing the daqsetup.bash script
                       for the version of NSCLDAQ you are using into your shell
                       (you can do this in your .bashrc).
                       Suppose, for example, I'm using the version of NSCLDAQ
                       installed in /usr/opt/daq/11.1-004:
                       I can:
   <a name="AEN15820"></a>```
   .   /usr/opt/daq/11.1-004/daqsetup.bash
   ```
2. Adding the appropriate -I option to your
                       compilation command line.  If you have performed step 1 above
                       this means adding -I$DAQROOT/include to your
                       compilation command.

Assuming you sourced the daqsetup.bash
            environment setup file, linking with the TCPIP library requires the following additions
            to your link command line:

<a name="AEN15828"></a>```
-L$DAQLIB -lTcp -lException -ldaqshm                    
                
```

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| TCPIP classes | Up | C++ encapsulation of a Tcl API subset |
