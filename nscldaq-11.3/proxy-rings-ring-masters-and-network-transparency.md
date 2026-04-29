|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 2. The Ring Buffer | Next |


---

# <a name="AEN99"></a>2.3. Proxy Rings, Ring Masters, and Network Transparency

## <a name="AEN101"></a>2.3.1. Proxy Rings

In a data data acquisition system we usually want several such computer
        systems to join the party.  Data taken in one system must be made
        visible in near real-time to analysis software in other computer
        systems.  This section describes the mechanism used by the NSCL Ring
        Buffer data acquisition system to accomplish this feat.

Each system that runs the ring buffer data acquisition system
        has a simple server process called the RingMaster.
        We'll talk more about the RingMaster and its role in the next
        section.

One role the ring master performs is to assist in hoisting
        data out of an local ring, sending it across the network to
        another system.  This is done through a mechanism called a
        *proxy ring* which makes the semantics
        of getting data from a remote system identical to the semantics
        of getting data from a local system.

If a process attempts to open a ring buffer whose URL does not
        specify localhost as the hostname, the ring buffer
        DAQ system contacts the RingMaster in the target host and collaborates
        with it to create a local ring and a network pipeline that
        ships data from the ring in the remote host to the local proxy ring.
        Only the first consumer goes through the gymnastics of creating a proxy
        ring and subsequent consumers simply connect to the proxy as an
        additional consumer. In this way, network traffic between rings and
        their proxies are aggregated.

A proxy ring has the local name hostname.remote-ringname
        where hostname is the host in which the
        'real ring' is located and remote-ringname
        is the name of the real ring in hostname.
        Thus the proxy ring for tcp://spdaq42/fox
        will be tcp://localhost/spdaq42.fox.

## <a name="AEN117"></a>2.3.2. The RingMaster server

All systems that run the Ring buffer data acquisition system
        also run a simple server called the RingMaster.
        The RingMaster performs the following functions:



- Collaborates with remote clients to set up a pipeline
              to produce data into proxy rings as described in the
              previous section.
- Allocate ring resources for local consumers.
- Cleans up when local consumer exit or release their
              ring resources.

The Ring buffer DAQ system has two types of clients.  Producers
        and consumers.  Recall that each ring can have at most one
        producer, and many consumers.

The ring master keeps track of which local processes are attached
        to a ring and whether or not a process is the producer or
        a consumer (actually a consumer could be consuming data from several rings,
        or even be more than one consumer on one ring).

When a client wants to obtain the put or a get pointer,
        it asks the ring master for one.  It does so by opening a
        TCP/IP connection to the ring master and sending it a pointer
        request message.  The ring master identifies the pointer
        it provides to the client.  The client is then required to hold
        the TCP/IP connection open.  If the TCP/IP connection closes,
        as it will normally  if a process exits, the RingMaster releases
        the pointer that was associated with that connection.

In this way, ring buffers are immune to stalls that could occur
        if a pointer got orphaned.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Data Transfer and Flow Control | Up | Ring buffer utilities |
