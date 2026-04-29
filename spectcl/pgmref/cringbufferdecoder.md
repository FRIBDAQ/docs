|  |  |  |
| --- | --- | --- |
| SpecTcl Programming Reference. |
| Prev |  | Next |


---

# <a name="AEN12492"></a>CRingBufferDecoder

<a name="AEN12496"></a>## Name

CRingBufferDecoder -- Decode data from ring buffers

<a name="AEN12499"></a>## Synopsis

```
#include <CRingBufferDecoder>
 
class CRingBufferDecoder : public CBufferDecoder
{
public:
  CRingBufferDecoder();
  virtual ~CRingBufferDecoder();

  virtual void operator()(UInt_t nBytes, Address_t pBuffer, CAnalyzer& rAnalyzer);

  virtual const Address_t getBody();
  virtual UInt_t getBodySize();
  virtual UInt_t getRun();
  virtual UInt_t getEntityCount();
  virtual UInt_t getSequenceNo();
  virtual UInt_t getLamCount();
  virtual UInt_t getBufferType();
  virtual UInt_t getPatternCount();
  virtual void   getByteOrder(Short_t& signature16,
			      Int_t&   signature32);
  virtual std::string    getTitle();
  virtual BufferTranslator* getBufferTranslator();

  virtual bool blockMode();	// True if data source must deliver fixed sized blocks.
  
  // Format helpers and stuff that gets you at what they know.
  

  bool  hasBodyHeader();
  void* getBodyHeaderPointer();
  void* getItemPointer();

  void  setFormatHelper(CRingFormatHelper* pHelper);
  void  setDefaultFormatHelper(CRingFormatHelper* pHelper);
  CRingFormatHelper* getCurrentFormatHelper();
  CRingFormatHelper* getDefaultFormatHelper();
  
  CRingFormatHelperFactory* getFormatFactory();
  
  // Members called that can invalidate the format helper:
  
  virtual void OnSourceAttach();
  virtual void OnSourceDetach();
  virtual void OnEndFile();
};       
        
```

<a name="AEN12501"></a>## DESCRIPTION

This class decodes data from NSCLDAQ 10.x and above.  Since the
            format of ring items differs between NSCLDAQ 10.x and NSCLDAQ 11.0 and
            above (11.0 introduces body headers to better support event building),
            this decoder relies on a `CRingFormatHelper`
            to deal with these differences.

When a data source is first opened with `-format` ring,
            you can use the **ringformat** command to specify
            the NSCLDAQ version used.  Alternatively, if you are certain
            that the data source will see the beginning of a run
            (not joining a run in progress on an online system), the
            class will use the presence (or absence) of a ring format item
            to select the appropriate format helper.   The absence of a ring
            format item selects the 10.x helper, while the version information
            in a ring format item will select the proper helper, if present.

Finally, the format helper can be set programmatically
            via the `setFormatHelper` and
            `setDefaultFormatHelper` methods, depending
            on what you are trying to do.

<a name="AEN12511"></a>## METHODS



`  CRingBufferDecoder();`Constructor.

` virtual   void operator()( UInt_t  nBytes,   Address_t  pBuffer,  CAnalyzer&  rAnalyzer);`Called whenever data has been received from the source.
                        This method breaks the `nBytes` bytes
                        of data in `pBuffer` into ring items.
                        Each item is then passed to the appropriate
                        method of `rAnalyzer`.

Note that since SpecTcl does fixed sizedd reads and
                        ring items are inherently variable sized, it is possible
                        for ring items to span from one buffer to the next.
                        This decoder recognizes this and mates partial ring items
                        at the end of each buffer with partial ring items at the
                        beginning of the next buffer.

Since ring items are atomically read from the ring buffer,
                        it must be possible to reconstruct ring items that have
                        been split across buffer boundaries as sampling is done
                        at the ring item leve, not the buffer level.

` virtual const   Address_t  getBody();`Returns the body of the ring item being processed.  Note
                        that if the nscldaq-11.x helper has been selected,
                        this will be a pointer to the data *following*
                        the body header.  Otherwise it will point just after
                        the ring item header, as 10.x does not have body headers.

The 11.x helper knows about the potential for zero length
                        body headers.

` virtual   UInt_t  getBodySize();`Returns the size of the ring item body.  Note that this
                        is the amount of data pointed to by the return value
                        from `getBody`.

To clarify, for the nscldaq 11.x helper, this value does
                        not include the size of the body header.  This choice was
                        made because the purpose of this method is to return
                        the number of bytes that must be processed by the
                        analyzer for data returned by
                        `getBody`.  The decoder
                        treats body headers as ancillary metadata for events that
                        can be retrieved by user code via special methods
                        provided by this class.

` virtual   UInt_t  getRun();`Returns the last run number seen.  Note that in
                        ring buffer NSCLDAQ systems, the run number is only
                        present in state change ring items.  If one of those
                        has not yet been seen, because SpecTcl is joining an
                        online run in progress, the run number returned will
                        be zero, or the most recent run from the prior data source,
                        if there was one.

` virtual   UInt_t  getEntityCount();`Returns the number of items in the data pointed to
                        by `getBody`.   Normally this
                        will be 1, however for scaler items,
                        this will be the number of scaler channels present in
                        the item.

` virtual   UInt_t  getSequenceNo();`Returns an approximation of the number of triggers seen.
                        NSCLDAQ 10.x don't maintain sequence numbers in ring items.
                        Instead periodically a ring item is emitted with trigger
                        statistics.  The value of this method is the
                        number of triggers for which data was emitterd for
                        this run, from the most recently received trigger count
                        item.  As the run evolves in time, this allows a
                        reasonable estimate of the analysis efficiency since
                        the percent error in the number of triggers will
                        go towards zero in the limit as the run time goes to
                        infinity.

` virtual   UInt_t  getLamCount();`Returns 0.

` virtual   UInt_t  getBufferType();`Returns the SpecTcl type of the item type currently
                        being processed.  For historical reasons these differ
                        from ring item types and are mapped as follows from
                        types in dataformat.h in NSCLDAQ
                        to buftypes.h:



- BEGIN_RUN maps to
                                  BEGRUNBF.
- END_RUN maps to
                                  ENDRUNBF.
- PAUSE_RUN maps to
                                  PAUSEBF.
- RESUME_RUN maps to
                                  RESUMEBF.
- PACKET_TYPES maps to
                                  PKTDOCBF.  Though I should
                                  point out that these items are rare in
                                  NSCLDAQ-10.x and later readouts.
- MONITORED_VARIABLES
                                  maps to RUNVARBF.  This
                                  is mostly used by NSCLDAQ 10.x and later
                                  when injection of EPICS data into the data stream
                                  is done as that's the known use-case now
                                  for these item types.
- PERIODIC_SCALERS this
                                  NSCLDAQ-11 type maps to
                                  SCALERBF.
- NSCLDAQ10::INCREMENTAL_SCALERS
                                  This NSClDAQ-10 type maps to
                                  SCALERBF.
- PHYSICS_EVENT maps to
                                  DATABF
- Any other type is not modified and will, therefore,
                                  cause `OnOther` to be
                                  called in the analyzer.

` virtual   UInt_t  getPatternCount();`Returns 0.

` virtual   void    getByteOrder( Short_t&  signature16,  Int_t&    signature32);`Returns byte order signatures for the current ring item.
                        Each ring item type is a 16 bit value in a 32 bit word
                        with the most significant bits (in the generating system)
                        zero.  This allows consuming systems to determine the
                        relative byte ordering and, therefore, generate
                        accurate generating byte order signatures.

` virtual   std::string     getTitle();`Returns the title from the last state change item.  If
                        no state change items have been seen yet (can happen
                        if SpecTcl starts analyzing on line data in the
                        middle of an active run), an empty string is returned.,

` virtual   BufferTranslator*  getBufferTranslator();`Returns a pointer to the buffer translator being used
                        to perform any byte order manipulations to transform
                        the data into the format used by the host executing
                        SpecTcl.

` virtual   bool  blockMode();`Returns false.  Ring buffer data
                        can  accept data buffers shorter than the requested
                        read size and this can (and probably will) happen at
                        the end of a run.

`   bool  hasBodyHeader();`If the item has a body header true
                        is returned, otherwise, `false`
                        is returned.  See also `getBodyHeaderPointer`.

`   void*  getBodyHeaderPointer();`Returns a pointer to the body header of a ring item.
                        If the ring item has no body header (NSCLDAQ 10.x) or has
                        a body header length of zero (NSCLDAQ 11.x item with no
                        body header), then a null pointer is returned.

`   void*  getItemPointer();`Returns a pointer to the ring item being processed.
                        In all versions this returns a pointer to the ring item
                        header.

`   void   setFormatHelper( CRingFormatHelper*  pHelper);`Replaces the current ring format helper with
                        `pHelper`.
                        `pHelper` must have been
                        created with new

Note that if
                        a ring format item is seen after this is called, the
                        ring format helper is destroyed and replaced by the
                        appropriate one.  Therefore it's recommended, instead,
                        to use `setDefaultFormatHelper`
                        to set a default ring format helper.

`   void   setDefaultFormatHelper( CRingFormatHelper*  pHelper);`Sets the default format helper to use for a new run
                        until (or unless) a format item is seen.  If a format
                        item is seen, that is used to select a (potentially)
                        new format helper.

Since NSCLDAQ 10 does not have ring format items,
                        it is wise to use the format helper
                        `CRingFormatHelper10` unless
                        you have good reason to believe that the software
                        will be analyzing NSCLDAQ 11.0 and later and will be
                        joining runs online in the middle of the run.

`   CRingFormatHelper*  getCurrentFormatHelper();`Returns a pointer to the format helper currently being
                        used by the decoder.

`   CRingFormatHelper*  getDefaultFormatHelper();`Returns a pointer to the default format helper currently
                        in effect.  Note that it is possible that the this does
                        not represent the active format helper, especially if
                        a ring format item was encountered that indicates a different
                        format helper should be u7sed.

`   CRingFormatHelperFactory*  getFormatFactory();`Returns a pointer to the ring format
                        helper factory
                        being used by this object.  The ring format
                        factory is responsible for selecting and creating
                        a ring format helper compatible with the data
                        that has been seen by the decoder.

` virtual   void  OnSourceAttach();`Called when a new data source is attached.  The
                        current buffer format helper is deleted and, for now,
                        the decoder falls back on the default buffer format
                        helper.

Once a ring format item is seen, (or rather if one
                        is seen), the ring format helper factory is used
                        to select an appropriate helper for the current
                        data source.  Furthermore, the format helper can be
                        set programmatically by calling
                        `setFormatHelper`.

` virtual   void  OnSourceDetach();`Called when  data source is detached. This invalidates
                        the current buffer format helper in much the same manner
                        as `OnSourceAttach`.

` virtual   void  OnEndFile();`Called when an end file is encountered on a data source.
                        This also invalidates the ring format helper.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CNSCLJumboBufferDecoder | Up | CRingFormatHelper |
