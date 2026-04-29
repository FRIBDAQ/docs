|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.bcnaf"></a>bcnaf

<a name="AEN15697"></a>## Name

bcnaf -- bcnaf via SBS VME CAMAC interfaces

<a name="AEN15700"></a>## Synopsis

**bcnaf `-ces | -wiener` *b c n a f* [d]
    **

<a name="AEN15706"></a>## DESCRIPTION

Performs the indicated CAMAC operation. The operation is defined by the
        `b, c, n, a, f` parameters that provide the CAMAC
        branch, crate, slot, subaddress and function code respectively. The
        optional `d` parameter provides the data for
        write operations (it is actually required for CAMAC write operations).

The command writes the data, Q and X responses to stdout.

<a name="AEN15712"></a>## OPTIONS



`-ces`Selects the CES CBD 8210 CAMAC Branch Highway Driver as the
                    CAMAC controller.

`-wiener`Selects the Weiner VC32/CC32 board set as the CAMAC
                    controller.

<a name="AEN15725"></a>## SEE ALSO

[[r15643]],

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| wienerbcnaf | Up | loadshaper |
