|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="CCAENV977"></a>CCAENV977

<a name="AEN44568"></a>## Name

CCAENV977 -- Software support for the CAEN V977 I/O register.

<a name="AEN44571"></a>## Synopsis

```
#include <CCAENV977.h>
            
```

```
  CCAENV977(ULong_t lBase, UShort_t nCrate = 0);
```

<a name="AEN44681"></a>## Description

The CAEN V977 is a 16 channel I/O register.  This software provides
                *policy independent* support for that module.
                Other software builds on top of this to e.g. use the module as a trigger
                or dead-time management module.

Refer to the CAEN hardware manual for the CAEN V977 for more information about this
                module.

<a name="AEN44686"></a>## Public member functions



<a name="AEN44691"></a>`CCAENV977 (ULong_t lBase, UShort_t nCrate);`

Constructs a `CCAENV977` object.  Once constructed,
                            you can use this object to manipulate the actual device described by
                            the constructor.

`lBase` is the base address of the module as
                            configured in the module's rotary switches. `nCrate`
                            is the VME crate in which you will insert the module.

<a name="AEN44709"></a>`UShort_t   inputSet (void);`

Reads the module input set register.  This module describes the
                            current latched state of the inputs. Note that the module allows you to
                            modify the latched set of inputs (e.g. you can clear bits from the
                            register as you process them.  See the overload of `inputSet`
                            described below.

<a name="AEN44720"></a>` void  inputSet (UShort_t value);`

Writes `value` to the input set register.

<a name="AEN44733"></a>`UShort_t   inputMask (void);`

Reads and returns the contents of the input mask register.  Bits set
                            in the input mask register disable the corresponding bits of the
                            input set register from being set as a result of hardware inputs.
                            It is possible, however for the input set register to be modified
                            arbitrarily by the software.
                            See the overload of `inputMask` below as well.

<a name="AEN44744"></a>` void  inputMask (UShort_t mask);`

Writes `mask` to the input mask register.
                            This allows you to disable the corresponding bits of the
                            input set register from responding to hardware inputs.

<a name="AEN44757"></a>` UShort_t  inputRead (void);`

This reads and returns the module's input read register.  The input
                            read register reflects the instantaneous state of the module inputs.
                            Note that since the input read register is not a latched register, in
                            general it's not very useful.

<a name="AEN44767"></a>` UShort_t  singleHitRead (void);`

The module is able to distinguish between single and multiple hits
                            in a gate for each input.  This register is has bits set for each channel
                            that has received a single hit.  The register is not affected by the
                            contents of the input mask register.

<a name="AEN44777"></a>` UShort_t  multihitRead (void);`

This register has bits set for each channel of the module that received
                            multiple input pulses during the gate time.  The register is not affecte
                            by the input mask register.  Multiple hits can also come about as a result
                            of writes to the input set register.

<a name="AEN44787"></a>`UShort_t   outputSet (void);`

Reads and returns the value of the output set register.  This is the set of
                            bits that is presented to the module's outputs.
                            To write this see the overloaded `outputMask`
                            function below.

<a name="AEN44798"></a>`void   outputSet (UShort_t pattern);`

Writes `pattern` to the output set register.

<a name="AEN44811"></a>`UShort_t   outputMask (void);`

Reads the output mask register.  The module outputs are the bitwise OR of the
                            output set register and the input Flip Flop latched value anded with the
                            complement of this mask register.  That is bits set in this register
                            prevent the inputs from setting their corresponding outputs.  The best description
                            of all of this is probably figure 3.1 in the CAEN hardware manual for
                            the module.

<a name="AEN44821"></a>`void   outputMask (Ushort_t mask);`

Writes a value to the output mask register. Each bit set in the mask
                            register disables the corresponding output bit from being controlled
                            by the inputs. See figure 3.1 in the CAEN V977 hardware manual for
                            more information about the function of the output mask register.

<a name="AEN44833"></a>`UShort_t   interruptMask (void);`

Reads the interrupt mask register.  Each bit of the input register
                            can cause an interrupt to occur. Setting bits in the mask register
                            disables the corresoponding input bit from causing an interrupt.
                            Note that NSCLDAQ does not require

<a name="AEN44843"></a>`void   interruptMask (UShort_t mask);`

Writes `mask` to the interrupt mask register.

<a name="AEN44856"></a>`void  outputClear (void);`

Clears the output flipflop channels.

<a name="AEN44866"></a>` UShort_t  singleHitReadAndClear (void);`

Returns the value of the single hit read-clear register.   This reads and
                            clears the single hit register.

<a name="AEN44876"></a>`UShort_t   multiHitReadAndClear(void);`

Reads and returns the value of the multihit read-clear register.  This
                            reads and resets the contents of the multihit flip-flop/register.

<a name="AEN44886"></a>`Ushort_t   serialNumber (void);`

Returns the serial number of the module.

<a name="AEN44896"></a>`UShort_t    firmwareLevel(void);`

Returns the module firmware revision level.  The firmware revision is divided
                            into a major and minor version (major.minor is the usual way to write this,
                            e.g. 3.4).  The most significant 8 bits of the firmware register are the
                            major revision, the least significatn 8 bits are the minor version.

<a name="AEN44906"></a>`void   controlRegister (void);`

Writes the control register.  It is an error to attempt to set bits that
                            have no meaning.  This is meant to ensure that you use the definitions
                            provided by the class for this (see "Types and public data" below).

<a name="AEN44916"></a>`UShort_t   controlRegister (void);`

Reads and returns the value of the control register.

<a name="AEN44926"></a>`void   Reset (void);`

Resets the module to its default setup.

<a name="AEN44934"></a>## Types and public data

The following constant values are defined to represent bits in the
                control register:



UShort_t `CCAENV977`::`control_Pattern`The Pattern bit in the control register.

UShort_t `CCAENV977`::`control_gateMask`The gateMask bit of the control register.

UShort_t `CCAENV977`::`control_OrMask`The Or mask bit of the control register.

<a name="AEN44959"></a>## Exceptions

Contract exceptions defined in the header DesignByContract.h
                can be thrown if the expectations of a function are violated by its caller.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CCAENV830 | Up | CCAMACScalerLRS2551 |
