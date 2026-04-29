|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  |  |


---

# <a name="manpage.vhqconfig"></a>vhqconfig

<a name="AEN67084"></a>## Name

vhqconfig --  Config file for

<a name="AEN67087"></a>## Synopsis

<a name="AEN67088"></a>**Example 1. Sample configuration file**

```
# vhq configuration file saved Tue Nov 15  13:28:47 EST 2005
       set  name  ppac_hv
       set  crate 0
       set base 0xdd00
       set maxv 2000
       set maxi 100
       set ILimit(a) 50
       set RampSpeed(a) 100
       set SetPoint(a) 1000
       set ILimit(b) 50
       set RampSpeed(b) 250
       set SetPoint(b) 1000
    
```

<a name="AEN67091"></a>## DESCRIPTION

The
            [[r10334]]
            application uses configuration files both to form a connection to vhq 2xx modules it
       is controlling and to load previously saved settings.  These configuration files are  Tcl  scripts  that
       set agreed upon variables to the needed configuration values.

       Configuration scripts have two sorts of variables Identification and Settings variables.  Identification
       variables identify the module both to humans and to computers, providing the  necessary  information  to
       connect  to  and  control the module.  Settings variables provide saved settings information that can be
       restored into a module once a connection to it has been established.

<a name="AEN67095"></a>### Identification Variables



nameProvides a human readable name for the module.

crateProvides the number of the VME crate in which the
                            module  is  stuffed.   If  not  provided,  this
                            defaults to zero.

baseProvides the base address (A16) at which the
                            module has been configured.  See the VHQ manuals for
                            more information on setting the module base address.
                            It is important not to configure  two  modules at
                            the same base address in the same VME crate.  This
                            variable is mandatory.

maxvDefines the maximum voltage the module can output
                            in volts.  This variable is mandatory.

maxiDefines the maxiumum current the module can
                            output in micro-Amps.  This variable is mandatory.

<a name="AEN67123"></a>### Settings Variables



Ilimit(channel)Sets  the current limit for channel.  The channel
                            index can be either
                            a or
                            b.
                            Recall that array
                            indices in Tcl are strings.  The units of measure
                            are micro-Amps

RampSpeed(channel)Sets the ramp speed for channel.  The channel index
                            can be either
                            a or
                            b.  The units  of  measure
                            are Volts/Sec.

SetPoint(channel)Sets the target voltage for the channel.  The
                            channel index can be either
                            a or
                            b.  Note that setting this
                            variable does not cause the module to perform a
                            ramp.  The units of measure are  Volts.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home |  |
| n568configfile | Up |  |
