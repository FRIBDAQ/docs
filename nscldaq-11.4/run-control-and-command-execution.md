|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 71. The actions library | Next |


---

# <a name="AEN12635"></a>71.3. Run Control and Command Execution

As was mentioned earlier in the overview, it is possible for a program
      using the actions library to initiate command execution in the tcl
      interpreter that spawned it. Because it is possible to end a run with the
      end proc, it is possible to force the run state to change. Those running
      data integrity checker programs in conjunction with the actions library may
      find this useful. The capabilities of the command execution is much more
      general than run control. Really, the limit of what can be done is at the
      limit of what the user can create with the TCL programming language.

One special case that is worth mentioning is when the ReadoutGUI that has
      been running the program is under remote control by a master ReadoutGUI.
      There is no difference in the behavior of the actions library for this
      scenario except that run control operations to end the run are forwarded
      to the master ReadoutGUI. In this way, there will not be scenarios when
      a single subsystem of the DAQ has shutdown. If the user chooses to
      propagate the end run to the master ReadoutGUI (via the EndRun function's
      argument), then they will be able to seamlessly run their DAQ while
      enslaved and not enslaved. However, if the user chooses not to forward to
      the master, they will need to add the following code to their
      ReadoutCallouts.tcl script to ensure that the local_end proc is defined.

```
      if {[llength [info proc local_end]]==0} {
        proc local_end {} {
          end
        }
      }
    
```

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| How does it work? | Up | Exemplified Usage of the Actions package |
