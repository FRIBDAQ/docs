|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 75. Event orderer and its user interface | Next |


---

# <a name="AEN16371"></a>75.2. Using the standard event orderer startup script

Since the event orderer is a library wrapped by Tcl commands, it is
            necessary to use a Tcl script to start the event orderer.  If the
            standard monitoringand user interface is sufficent, you can use the
            *standard event orderer startup script*..
            If the data acquisition system is installed in DAQROOT,
            you can start the event orderer using the standard startup script:

<a name="AEN16376"></a>```
$DAQROOT/bin/startOrderer
            
```

It is also possible to start up more than one event orderer.  Each
           event orderer must have a unique name.  Supply that name on the
           command line e.g.:

<a name="AEN16379"></a>```
$DAQROOT/bin/startOrderer  aName
           
```

Event orderer names are automatically qualified by your login name.
          There is therefore no supported way to connect clients to another
          user's event orderer.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Event orderer and its user interface | Up | Writing an event orderer startup script |
