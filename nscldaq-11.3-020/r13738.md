|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="evb1_evb_cconnectionlist"></a>EVB::connectionList

<a name="AEN13752"></a>## Name

EVB::connectionList -- List event builder connections

<a name="AEN13755"></a>## Synopsis

**package require EVB::connectionList
            **

**EVB::connectionList *window ?options?*
**

<a name="AEN13761"></a>## DESCRIPTION

Provides an auto updating widget that displays the set of data
            source connection clients that are attached to the event builder
            fragmento orderer.  Creating the widget also schedules a repeating
            task to update the contents of the widget.

The widget displays a table with several columns:



HostIP address of connected clients

DescriptionThe connection description sent to the server when the
                    client connected.

StateThe connection state of the client

StalledIndicates if the source has not sent fragments
                    recently while other sources have.

<a name="AEN13782"></a>## OPTIONS



`-updaterate`The number of seconds between updates
                            (must be an integer).

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| EVB::CallbackManager | Up | EVB::GUI procs |
