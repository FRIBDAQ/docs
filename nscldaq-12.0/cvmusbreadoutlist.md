|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="vmusb3-cvmusbreadoutlist-swig"></a>cvmusbreadoutlist

<a name="AEN91191"></a>## Name

cvmusbreadoutlist -- SWIG wrappers for `CVMUSBReadoutList`

<a name="AEN91195"></a>## Synopsis

**Construction. **

```
                ::cvmusbreadoutlist::CVMUSBReadoutList name
             
                ::cvmusbreadoutlist::CVMUSBReadoutList name -this ptr
             
                     
```

**Simple VME/register operations. **

```
            object addRead16 address amod
             
            object addRead32 address amod
             
            object addRead8 address amod
             
            object addRegisterRead address
             
            object addRegisterWrite address data
             
            object addWrite16 address amod data
             
            object addWrite32 address amod data
             
            object addWrite8 address amod data
             
            
```

**Block transfer operations. **

```
            object addBlockRead32 base amod transfers
             
            object addFifoRead16 address amod transfers
             
            object addFifoRead32 address amod transfers
             
            object addMaskedCountBlockRead32 base amod
             
            object addMaskedCountFifoRead32 address mask amod
             
            object addBlockCountRead16 address mask amod
             
            object addBlockCountRead32 address mask amod
             
            object addBlockCountRead8 address mask amod
             
            
```

**Miscellaneous methods. **

```
        object addMarker value
             
    object addDelay cycles
             
        object clear
             
        object get
             
        object size
             
        ::cvmusbreadoutlist::CVMUSBReadoutList_uint32_vector_get v i
             
        ::cvmusbreadoutlist::CVMUSBReadoutList_uint32_vector_size v
             
        
```

**Variables. **

```
::cvmusbreadoutlist::CVMUSBReadoutList_a16Priv
```

<a name="AEN91324"></a>## DESCRIPTION

This package encapsulates a `CVMUSBReadoutList`
                    class/object.  The class allows you to create instances
                    of VME operation lists.  Once created, you can add
                    operations to that list that can either be executed
                    immediately or stored fro execution in data taking mode
                    in response to an appropriate trigger.

For more information about this class and its methods,
                    see METHODS below.  The class also defines a set of
                    variables that contain the VME address modifier values.
                    See VARIABLES for information about those.

<a name="AEN91329"></a>## METHODS

**Construction. **
                        Two construction mechanisms are provided.  The first
                        creates an empty list.  The second creates an object
                        that wraps itself around a pointer to an existing list.

Constructed objects appear like a command ensemble who's
                    base command name is the `name` parameter
                    to the constructor command.  If the special name
                    %AUTO is specified, the constructor will
                    assign a unique name.  In all cases the base name of the
                    command ensemble (or object name) is returned by the constructor.



**::cvmusbreadoutlist::CVMUSBReadoutList *name*
**

Constructs an empty list object named `name`
                        (see the discussion above however).  The name of the object
                        is returned by this command.

**::cvmusbreadoutlist::CVMUSBReadoutList *name* -this *ptr*
**

Constructs an object around an existing pointer to a
                        list object.  The name of the object is
                        `name` and `ptr`
                        is a SWIG type safe pointer.  Type-safe pointers are
                        just the address of a C++ object as a string that has
                        been decorated with information about the type of the
                        object.

A type-safe pointer to a readout list is passed to a Tcl
                        driver's `addReadoutList`
                        sub-command.

**Simple VME/register operations. **
                    This group of methods add single shot VME operations
                    and register transfers to a list.  A VME operation is
                    specified by both an address and an address modifier.
                    The address modifier selects a specific address space.
                    See
                    [http://en.wikipedia.org/wiki/VMEbus](http://en.wikipedia.org/wiki/VMEbus)
                    for a table of address modifiers and their meaning.

`cvmusbreadoutlist` also defines
                    some variables that contain these address modifiers.
                    See VARIABLES below for a description of those
                    variables.



** *object* addRead16 *address amod*
**

Adds a 16 bit read from the address and address modifier
                    specified by `address` and
                    `amod` respectively.  The data
                    are put in either the output buffer if the read is performed
                    by `cvmsub::executeList` or in the
                    event buffer if the list is triggered in data acquisition
                    mode.

** *object* addRead32 *address amod*
**

Same as `addRead16` however the
                    data transfer width is 32 bits.  The list performs
                    the operation in little endian order.   That is the
                    low order part of the longword is placed in the
                    output/event buffer prior to the upper order bits.

** *object* addRead8 *address amod*
**

Same as `addRead16` however only
                    the data emitted consists of 8 bits of data in the low order
                    8 bits of a 16 bit word.

** *object* addRegisterRead *address*
**

Adds a read of an internal register to the stack.
                    The `address` parameter specifies
                    which register to read.  This is a number that should be
                    taken from the table in section 3.4 of the VM-USB
                    manual.

** *object* addRegisterWrite *address data*
**

Adds a register write to the list.  `address`
                    specifies the register address (taken from the table in
                    section 3.4 of the VM-USB manual), `data`
                    is the value to write.

** *object* addWrite16 *address amod data*
**

Writes the 16 bit `data` to the VME
                    location specified by `address`
                    and `amod`.  If there are bits set
                    above the least significant 16 bits of `data`,
                    they are ignored.

** *object* addWrite32 *address amod data*
**

Same as for `addWrite16` however 32 bits of
                    `data` are written.

** *object* addWrite8 *address amod data*
**

Same as `addWrite16` however only the
                    least significant 8 bits are written.

**Block transfer operations. **
                    The VM-USB is capable of several types of block transfer
                    operations.  If the address modifier is a block transfer
                    address modifier, the VM-USB will take advantage of that
                    mode of transfer.

VME block transfer operations allow a significant
                    improvment in performance by reducing the number of address
                    cycles asserted on the bus by the master.  Specifically,
                    in steady state operation, an address is only cycled on the
                    bus as the transfer address crosses a 256 byte address
                    boundary.  In between these boundaries, slave boards that
                    support block transfers are assumed to maintain counters
                    that keep track of the transfer offset within the 256 byte
                    page.

In addition to block transfer operations as described above,
                    the VM-USB also supports FIFO block transfers.   A FIFO
                    block transfer is just a block transfer that always asserts
                    the base address when an address cycle is required.

Finaly the VM-USB also supports block transfers whose
                    size depends on a bit field in a value read from the VME
                    bus.



** *object* addBlockRead32 *base amod transfers*
**

Adds a block read that is 32 bits wide tyo the stack.
                    The first transfer address is `base`,
                    transfers are all done with `amod` as
                    the address modifier.  `transfers`
                    operations are performed (transers*sizeof(uint32_t) bytes), unless
                    a transfer causes a bus error.

If a transfer triggered a bus error, a 0xffffffff
                    is placed in the output/event buffer and the transfer terminates.
                    Note that if the last transfer was a bus error and the data
                    in a successful transfer might have been a 0xffffffff,
                    there is some ambiguity about how the transfer actually terminated.
                    If you expect that the tranfer might be terminated by a bus
                    error "normally", ber sure to specify a transfer count very
                    much in exceess of what you might reasonably expect to get.

** *object* addFifoRead16 *base amod transfers*
**

Adds a 16 bit FIFO read to the list.  All transfers are
                    performed from `base` with the
                    `amod` address modifier.
                    At most `transfers` transfers are performed.
                    In the even to of a bus error, a marker value;
                    0xffff will be inserted in the
                    read/event buffer, and the transfer will terminate.

** *object* addFifoRead32 *base amod transfers*
**

Same as `addFifoRead16` however
                    each read transfers 32 bits of data.

** *object* addBlockCountRead16 *address mask amod*
**

Adds a 16 bit read that extracts the transfer count for the
                    next variable block read.   A 16 bit read is performed from
                    the location specified by `address` and
                    address modifier `amod`.  The
                    bits that are set in `mask` determine the final
                    actual value of the transfer count (bits set in
                    `mask` matter unset bits don't).

** *object* addBlockCountRead32 *address mask amod*
**

Same as `addBlockCount16` however
                    the tranfer is 32 bits wide.

** *object* addBlockCountRead8 *address mask amod*
**

Same as `addblockCountRead16` but the
                    transfer is 8 bits.

** *object* addMaskedCountBlockRead32 *base amod*
**

Adds a variable block read operation to the VME operation
                    list.  The last block count read by one of the
                    `addBlockCountReadxxx` methods'
                    above is used as the transfer count.    The base address
                    of the transfer is `base`
                    and all transfers are done with the `amod`
                    address modifier.

The normal rules for bus error termination of block transfers
                    apply.

** *object* addMaskedCountFifoRead32 *base amod*
**

Same as `addMaskedCountBlockRead32`,
                    however any needed address cycles always place
                    `base` on the address bus.  This
                    makes this method usable to get data from a FIFO register.

**Miscellaneous methods. **
                The methods in this section don't fit into any other category.
                Where the method is not a subcommand of a `object`
                it is a static method of the class.



** *object* addMarker *value*
**

Adds a command to put a literal marker for
                `value` in to the buffer/event.

** *object* addDelay *cycles*
**

Adds a delay to the list.  When this instruction is executed,
            stack execution stalls for `cycles` cycles where
            one cycle is 200ns.    The maximum wait time is 255 cycles, however
            you can insert more than one wait operation to get longer waits.

** *object* clear
            **

Clears the list

** *object* get
            **

Returns a vector to a uint32 where each vector element is one
                32 bit stack line.  See below for static methods to get
                information about/from this vector.

** *object* size
            **

Returns the number of 32 bit stack lines in the object.

**::cvmusbreadoutlist::CVMUSBReadoutList_uint32_vector_get *v i*
**

Given a vector `v` retrived from
                the `get` method tells you  how many
                elements it contains.

**::cvmusbreadoutlist::CVMUSBReadoutList_uint32_vector_size *v*
**

Given a vector `v` gotten from
                `get` returns the nmber of 32 bit entities
                 in the vrctor.

<a name="AEN91600"></a>## VARIABLES

The `cvmusbreadoutlist` class provides
                    several variables that define the various address modifiers
                    symbolcally:



`::cvmusbreadoutlist::CVMUSBReadoutList_a16Priv`Defines the address modifier for 16 bit address
                                widths privilege access.  16 bit address space
                                is often refered to as shortio as  well.

`::cvmusbreadoutlist::CVMUSBReadoutList_a16User`Same as above, however accesses are in user
                                mode rather than privileged transfer mode.

`::cvmusbreadoutlist::CVMUSBReadoutList_a24PrivBlock`Defines the address modifier for A24
                                    privileged block transfers.  Block transfers
                                    are a mechanism the VME bus defines for
                                    reducing the number of address cycles required
                                    to transfer a contiguous block of data.

A24 bit addressing mode is also called
                                    standard addressing.

`::cvmusbreadoutlist::CVMUSBReadoutList_a24PrivData`Defines the address modifier for 24
                                        bit wide addressing of privileged data.
                                        A24 address modes are also called
                                        standard addressing.

`::cvmusbreadoutlist::CVMUSBReadoutList_a24PrivProgram`Same as above, however the
                                            addressing is to privileged progfam space.

`::cvmusbreadoutlist::CVMUSBReadoutList_a24UserBlock`Defines the address modifier for
                                                24 bit wide address block transfers.

`::cvmusbreadoutlist::CVMUSBReadoutList_a24UserData`Defines the address modifier for 24 bit wide
                                user data transfers.

`::cvmusbreadoutlist::CVMUSBReadoutList_a24UserProgram`Defines the address modifier for 24 bit wide
                                user program space.

`::cvmusbreadoutlist::CVMUSBReadoutList_a32PrivBlock`Defines the address modifier for 32 bit privileged
                            block transfers.

`::cvmusbreadoutlist::CVMUSBReadoutList_a32PrivData`Defines the address modifier for 32 bit wide
                                privileged data transfers.  32 bit addressing is
                                sometimes called *extended addressing*.

`::cvmusbreadoutlist::CVMUSBReadoutList_a32PrivProgram`Defines the address modifier for 32 bit privileged
                            program accesses.

`::cvmusbreadoutlist::CVMUSBReadoutList_a32UserBlock`Defines the address modifier for 32 bit user
                            block transfers.

`::cvmusbreadoutlist::CVMUSBReadoutList_a32UserData`Defines the address modifier for 32 bit user
                                data transfers.

`::cvmusbreadoutlist::CVMUSBReadoutList_a32UserProgram`Defines the address modifier for 32 bit user
                                    program access.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| cvmusb | Up | Module |
