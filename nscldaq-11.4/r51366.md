|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN51366"></a>CZMQDealerTransport

<a name="AEN51370"></a>## Name

CZMQDealerTransport -- Peer, receiver for CZMQRouterTransport(3daq)

<a name="AEN51373"></a>## Synopsis

```
 
#inclucde <CZMQDealerTransport.h>
class CZMQDealerTransport : public CFanoutClientTransport
{

public:
    CZMQDealerTransport(const char* pUri);
    CZMQDealerTransport(const char* pUri, uint64_t id);
    
    void recv(void** ppData, size_t& size);
    void send(iovec* parts, size_t numParts);
    void setId(uint64_t id);

};

        
```

<a name="AEN51375"></a>## DESCRIPTION

The ZMQ Router/Dealer communication pattern provides
            mechanism to fan work units out to parallel workers.
            The Router, whose transport is
            `CZMQRouterTransport`(3daq)
            is the fanout.  The workers receive data via this
            class.

The transports hide the details of requesting data
            and stripping delimeters.  From the users's point of
            view the worker just does a call to
            `recv` and a work unit is
            returned.

<a name="AEN51381"></a>## METHODS

`CZMQDealerTransport` is a
            unidirectional transport that can only receive data.



`  CZMQDealerTransport(const  char* pUri);`This constructor just supplies
                        `pUri` the
                        ZMQ URI specifying the communication
                        endpoint agreed upon by the Router and
                        Dealer.

This method of construction requires that
                        you call
                        `setId` 
                        to establish the client id prior to
                        transferring data with
                        `recv`.

`  CZMQDealerTransport(const  char*  pUri, uint64_t  id);`This constructor supplies both the
                        endpoint URI (`pUri`),
                        and the client id;
                        `id`.

`   void  recv(void**  ppData, size_t&  size);`Receives data from the peer.  The process
                        of requesting data, receiving the multipart
                        message, stripping the delimeter and
                        reassembling the message payload into
                        a single blob is done
                        by this method, transparent to the caller.

`send`This is not a legal method.
                        If you call this,
                        a `std::logic_error`
                        is thrown.

`   void  setId(uint64_t  id);`

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CZMQRouterTransport | Up | CDataSinkElement |
