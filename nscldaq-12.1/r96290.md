|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN96290"></a>sis_vmusb_interface

<a name="AEN96303"></a>## Name

sis_vmusb_interface -- Use SIS module software over VMUSB

<a name="AEN96306"></a>## Synopsis

```
#include <sis_vmusb_interface.h>

class sis_vmusb_interface : public vme_interface_class {
public:
    virtual int vmeopen( void ) ;
	virtual int vmeclose( void ) ;

	virtual int get_vmeopen_messages( CHAR* messages, UINT* nof_found_devices ) ;

	virtual int vme_A32D32_read( UINT addr, UINT* data ) ;

	virtual int vme_A32DMA_D32_read (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words ) ;
	virtual int vme_A32BLT32_read (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words ) ;
	virtual int vme_A32MBLT64_read (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words ) ;
	virtual int vme_A32_2EVME_read (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words ) ;
	virtual int vme_A32_2ESST160_read (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words ) ;
	virtual int vme_A32_2ESST267_read (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words ) ;
	virtual int vme_A32_2ESST320_read (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words ) ;

	virtual int vme_A32DMA_D32FIFO_read (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words ) ;
	virtual int vme_A32BLT32FIFO_read (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words ) ;
	virtual int vme_A32MBLT64FIFO_read (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words ) ;
	virtual int vme_A32_2EVMEFIFO_read (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words ) ;
	virtual int vme_A32_2ESST160FIFO_read (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words ) ;
	virtual int vme_A32_2ESST267FIFO_read (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words ) ;
	virtual int vme_A32_2ESST320FIFO_read(UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words ) ;


	virtual int vme_A32D32_write( UINT addr, UINT data ) ;
	virtual int vme_A32DMA_D32_write (UINT addr, UINT* data, UINT request_nof_words, UINT* written_nof_words ) ;
	virtual int vme_A32BLT32_write (UINT addr, UINT* data, UINT request_nof_words, UINT* written_nof_words ) ;
	virtual int vme_A32MBLT64_write (UINT addr, UINT* data, UINT request_nof_words, UINT* written_nof_words ) ;

	virtual int vme_A32DMA_D32FIFO_write (UINT addr, UINT* data, UINT request_nof_words, UINT* written_nof_words ) ;
	virtual int vme_A32BLT32FIFO_write (UINT addr, UINT* data, UINT request_nof_words, UINT* written_nof_words ) ;
	virtual int vme_A32MBLT64FIFO_write (UINT addr, UINT* data, UINT request_nof_words, UINT* written_nof_words ) ;

	virtual int vme_IRQ_Status_read( UINT* data ) ;


};


            
```

<a name="AEN96308"></a>## DESCRIPTION

Some Struck (SIS) modules have support provided in the form of a class that
                performs VME operations via a class derived from `vme_interface_class`.
                `sis_vmusb_interface` provides a version of that class built on top of
                `CVMUSB`.  To use this class, the variable:
                `Globals::pUSBController` must be a pointer to an instance of a
                `CVMUSB` object.  In the VMUSBReadout skeleton, when the program is
                connected to a VMUSB, this will be the case.  If using this class outside that
                framework, you software will need to take care of this requirement.

All methods of this class return 0 on success and some negative
                value on failure.  Some methods are no-ops but provided to satisfy the requirements
                of the class interface.

<a name="AEN96318"></a>## METHODS



` int vmeopen
                            ();`This, rather than opening a connection to the VMUSB, will, instead, return
                        0 if there's already a non-null pointer in `Globals::pVMUSBController`.
                        If that pointer  is null, -1 is returned.

` int vmeclose
                            ();`This method is a no-op that always return success (0).

` int get_vmeopen_messages
                            (char* messages, UINT* nof_found_devices);`It's not actually clear what this is supposed to do in the SIS base class (that class
                        is completely undocumented), however what *we* do is:



- always return 0
- If `Globals::pUSBController` is not null,
                                  set the value of `*nof_found_devices` to 1 and copy the
                                  string Open will succeed to `*messages`.
                                  If `Globals::pUSBController` is null, sets the value of
                                  `*nof_found_devicdes` to 0 and `*messages`
                                  to There's no underlying VMUSB object to use


This method can, therefore, be used to determine if a call to 
                            `vmeopen` will succeed.

` int vme_A32D32_read
                            (UINT addr, UINT* data);`Does a 32 bit read from the VME bus at `addr`.  The read is done
                        with the address modifier `CVMUSBReadoutList::a32UserData`.
                        On success the return value  is 0 and the data read are stored into `*data`

` int vme_A32DMA_D32_read(UINT addr, UINT* data, UINT req_nof_words, UINT* got_nof_words);`Peforms a block transfer starting from `addr` on the VME bus.
                        The size of each transfer is 32 bits and the transfer is done with the
                        `CVMUSBReadoutList::a32UserBlock` address modifier.
                        Data read are stored sequentially in `data`. `data`
                        Must point to a block of storage that is at least `req_nof_words`
uint32_t units long.   The transfer terminates when either
                        `req_nof_words` 32 bit items are transferred or a bus error occurs,
                        whichever is first.  The actual number of transfers is stored into `*got_nof_words`

The method returns success (0), if any data are transferred.

` int vme_A32BLT32_read
                            (UINT addr, UINT* data, UINT req_nof_words, UINT* got_nof_words);`In this implementation, this is synonymous with `vme_A32DMA_D32_read`.
                        I imagine the reason for the differencde in the original class was to support block transfers without
                        BLT address modifiers.  The VMUSB, however only does block reads if tiven a block transfer address.
                        modifier.  If required, in the future, `vme_A32DMA_D32_read` can be re-implemented
                        as a single transfer loop.

` int vme_A32MBLT64_read
                            (UINT addr, UINT* data, UINT req_nof_words, UINT* got_nof_words);`Peforms 64 bit block transfers (supposedly supported by the VMUSB).  These are
                        done using address modifier 0x0c which is  a64 bit BLT user space
                        transfer.  All of the parameters are the same as the 32 bit transfer but the transfer
                        unit is uint64_t.

` int vme_A32_2EVME_read 
                            (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words);`
` int vme_A32_2ESST160_read
                            (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words);`
` int vme_A32_2ESST320_read
                            (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words);`
` int vme_A32_2ESST267_read
                            (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words);`These methods represent 64 bit high speed transfer methods that are not
                        supported by the VMUSB.  As such, they are synonyms for 
                        `vme_a32MBLT64_read`

` int vme_A32DMA_D32FIFO_read
                            (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words);`Peforms a 32 bit read from a FIFO.  This acts identically to 
                        a block transfer, however the address is not incremented after each read.

` int vme_A32BLT32FIFO_read
                            (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words);`Peforms a 32 bit read from a FIFO.  This acts identically to 
                        a block transfer, however the address is not incremented after each read.

` int vme_A32MBLT64FIFO_read
                            (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words);`Peforms a 64 bit read from a FIFO.  This acts identically to 
                        a block transfer, however the address is not incremented after each read.

` int vme_A32_2EVMEFIFO_read
                            (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words);`
` int vme_A32_2ESST160FIFO_read
                            (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words);`
` int vme_A32_2ESST267FIFO_read
                            (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words);`
` int vme_A32_2ESST320FIFO_read
                            (UINT addr, UINT* data, UINT request_nof_words, UINT* got_nof_words);`These are FIFO reads that are unsupported by the VMUSB.  They are implemented
                        as calls to `vme_A32MBLT64FIFO_read`

` int vme_A32D32_write
                            (UINT addr, UINT data);`Performs a 32 bit write
                        of `data` to `addr`.
                        The address modifier used is 
                        `CVMUSBReadoutList::a32UserData`

` int vme_A32DMA_D32_write
                            (UINT addr, UINT* data, UINT request_nof_words, UINT* written_nof_words);`
` int vme_A32BLT32__write
                            (UINT addr, UINT* data, UINT request_nof_words, UINT* written_nof_words);`
` int vme_A32MBLT64_write
                            (UINT addr, UINT* data, UINT request_nof_words, UINT* written_nof_words);`The `CVMUSB` class does not support block transfer writes.
                        These methods are implemented in `vme_A32DMA_D32_writre` as a
                        write loop and the other methods are implemented as calls to that method.

` int vme_A32DMA_D32FIFO_write
                            (UINT addr, UINT* data, UINT request_nof_words, UINT* written_nof_words);`
` int vme_A32BLT32FIFO_write
                            (UINT addr, UINT* data, UINT request_nof_words, UINT* written_nof_words);`
` int vme_A32MBLT64FIFO_write
                            (UINT addr, UINT* data, UINT request_nof_words, UINT* written_nof_words);`Does block writes to a FIFO, that is the address of the write does not
                        increment after each write.   Note that since `CVMUSB` does
                        not implement FIFO write operations, these are implemented as individual writes in a 
                        loop to the same address.

` int vme_IRQ_Status_read
                            (UINT* data);`Reaing the VME interrupt status is not supported by the VMUSB, 
                        therefore, this method throws an `std::runtim_error`
                        when called.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CControlHardware | Up | cvmusb |
