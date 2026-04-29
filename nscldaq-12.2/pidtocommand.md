|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="python3.pidtocommand"></a>pidtocommand

<a name="AEN85776"></a>## Name

pidtocommand -- Convert a PID into its command string

<a name="AEN85779"></a>## Synopsis

```
from nscldaq.pidtocommand import pidToCommand

print('Init is run as:', ' '.join(nscldaq.pidToCommand(1)))

        
```

<a name="AEN85781"></a>## DESCRIPTION

Given a valid process id (integer), returns the command line string
            that started that process. The command line is returned as an
            indexable  iterable
            where each item is is a consecutive command word.  If the pid is invalid,
            a KeyError is raised.

To support getting process command lines from remote systems
            (e.g. for the **ringdiagnostics**), this is also
            installed in $DAQBIN and, when invoked as a command, takes a
            single parameter, the process id, and outputs that PID's command line.
            The command line is output as a string.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| PortManager | Up | nscldaqutils |
