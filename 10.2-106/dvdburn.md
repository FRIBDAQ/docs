|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.dvdburn"></a>dvdburn

<a name="AEN10681"></a>## Name

dvdburn -- Command line tool to burn NSCLDAQ data DVDs.

<a name="AEN10684"></a>## Synopsis

**dvdburn [firstrun [lastrun]]
	**

<a name="AEN10689"></a>## DESCRIPTION

Burns the data associated with a set of runs to DVD.
        The [[r64299]]
        package is used to do the burn, so all restrictions and dependencies
        for that package apply.

If no parameters are supplied, all runs are burned.  If
        `firstrun` is supplied, all runs with run numbers
        at least `firstrun` are burned.
        Finally if both `firstrun` and `lastrun`
        are supplied, all run numbers that are at least `firstrun`
        and at most `lastrun` are burned.

<a name="AEN10700"></a>## Dependencies

See
            [[r64299]].

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| serverauth | Up | burngui |
