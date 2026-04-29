|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="daq1.mg_startloggers"></a>mg_startloggers

<a name="AEN17077"></a>## Name

mg_startloggers -- Start Event Managed Event Loggers

<a name="AEN17080"></a>## Synopsis

**$DAQBIN/mg_startloggers *manger-host manager-user*
**

<a name="AEN17084"></a>## DESCRIPTION

Requests that the manager run by the user *manager-user*
            in the system *manager-host* start all
            appropriate event loggers.  The manager will only start event loggers
            if the global recording state is on.  Individual loggers will
            only be started if they are enabled.

Each started logger will log exactly one run and then exit.
            Therefore loggers should be started early in a
            sequence that is triggered by BEGIN transitions.

Output from loggers is relayed to the output monitor where
            [[r16891]]
            will display it if run.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| EVBMonitor | Up | rdo_runFromKv |
