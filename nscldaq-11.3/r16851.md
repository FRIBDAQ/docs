|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.cesbcnaf"></a>cesbcnaf

<a name="AEN16865"></a>## Name

cesbcnaf -- CAMAC operation via a CES CAMAC interface

<a name="AEN16868"></a>## Synopsis

**cesbcnaf *b c n a f* [d]
    **

<a name="AEN16873"></a>## DESCRIPTION

Performs the indicated CAMAC operation. The operation is defined by the
        `b, c, n, a, f`
        parameters that provide the CAMAC branch, crate, slot, subaddress and
        function code respectively.
        The optional `d` parameter provides the data for
        write operations (it is actually required for CAMAC write operations).

The command writes the data,
        `Q` and `X` responses to stdout.

<a name="AEN16881"></a>## SEE ALSO

[[r16886]],
        [[r16921]]

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| loadcfd | Up | wienerbcnaf |
