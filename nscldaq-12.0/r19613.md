|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="daq1.lg_selshift"></a>lg_selshift

<a name="AEN19617"></a>## Name

lg_selshift -- Select the current shift

<a name="AEN19620"></a>## Synopsis

**lg_selshift [*shift-name*]
         **

<a name="AEN19625"></a>## DESCRIPTION

The **lg_*** family of commands have the concept
            of a *current shift* (or on duty shift).
            All automatically logged state changes attribute the shift to
            the on-duty shift.  This command provides a mechanism to set the
            current shift.  If `shift-name` is not supplied,
            a shift selection dialog is displayed. Note that this dialog can
            remain displayed after the current shift is selected, providing for
            a permanently visible shift change dialog.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| lg_mgshift | Up | lg_kvstore |
