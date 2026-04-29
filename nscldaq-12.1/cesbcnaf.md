|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.cesbcnaf"></a>cesbcnaf

<a name="AEN26599"></a>## Name

cesbcnaf -- CAMAC operation via a CES CAMAC interface

<a name="AEN26602"></a>## Synopsis

**cesbcnaf *b c n a f* [d]
    **

<a name="AEN26607"></a>## DESCRIPTION

Performs the indicated CAMAC operation. The operation is defined by the
        `b, c, n, a, f`
        parameters that provide the CAMAC branch, crate, slot, subaddress and
        function code respectively.
        The optional `d` parameter provides the data for
        write operations (it is actually required for CAMAC write operations).

The command writes the data,
        `Q` and `X` responses to stdout.

<a name="AEN26615"></a>## SEE ALSO

[[r26620]],
        [[r26655]]

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| loadcfd | Up | wienerbcnaf |
