|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="ccusb3-addtcldriver"></a>addtcldriver

<a name="AEN70006"></a>## Name

addtcldriver -- Register Tcl command ensemble as a device module

<a name="AEN70009"></a>## Synopsis

**addtcldriver *tcl-command*
**

<a name="AEN70013"></a>## DESCRIPTION

Registers the base of a Tcl command ensemble (e.g. an object
            instance command) as a device module that can be used in
            module lists such as the `-modules` option of a
            **stack** command.

The `tcl-command` is the command
                to register.

<a name="AEN70020"></a>## EXAMPLE

The command below:

<a name="AEN70023"></a>```
addtclcommand sometclinstance
                
```

Registers the Tcl command **sometclinstance**
                as a module.  The name of the module is the same as the
                name of the command (sometclinstance).

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| 3ccusb | Up | ad811 |
