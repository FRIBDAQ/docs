|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="daq1.mg_shutdown"></a>mg_shutdown

<a name="AEN17281"></a>## Name

mg_shutdown -- Shutdown the DAQ manager.

<a name="AEN17284"></a>## Synopsis

**$DAQBIN/mg_shutdown *host user*
**

<a name="AEN17288"></a>## DESCRIPTION

Tries to shut down the DAQ manager that's runing in the system
            *host* started by *user*.
            By "tries to shutdown" we mean that the program attempts to ask the
            manager to shutdown via its REST server interface.  As long as that
            interface is working there's a good chance this shutdown will succeed.

The shutdown process consists of invoking a
            SHUTDOWN transition,
            if the state is not already SHUTDOWN.
            Once that transition has completed, the server exits.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| mg_startManager | Up | mg_kvget |
