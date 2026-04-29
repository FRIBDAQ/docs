|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="vmusb3-CBDCamacBranch"></a>CBDCamacBranch

<a name="AEN71279"></a>## Name

CBDCamacBranch -- run a CAMAC branch through a CES CBD8210 bridge

<a name="AEN71282"></a>## Synopsis

**CBDCamacBranch create *name base*
**

**CBDCamacBranch config *name option value ...*
**

**CBDCamacBranch cget *name*
**

<a name="AEN71292"></a>## DESCRIPTION

When the user intends to read out CAMAC devices through the VM-USB this driver can be used if the branch driver is a CES CBD8210. This class maintains a camac branch driver object that must encapsulate the necessary functionality for controlling the CAMAC devices on its branch. The camac branch driver essentially provides the means for translating standard bcnaf commands to VME commands that are executable by the VM-USB in a command stack. It must also properly implements the CCamacBranchDriver interface.

A CAMAC branch is just a bunch of CAMAC crates strung together with a common branch number. For this reason, the CBDCamacBranch must be told which branch number it is operating on and also the camac crates that exist on the branch. Be sure that the camac crates registered to the branch are consistent with the driver being used by the CBDCamacBranch. In other words, modules prefixed by CBD, like CBDCamacCrates, must be registered to the CBDCamacBranch if the driver has been defined as a CES CBD8210.

At initialization the following operations occur:



1. Setup the appropriate camac branch driver
2. The branch driver will initiate the branch
3. Call initialize for each crate registered to the branch


At the end of the run, the specific end of run operations are called for each crate registered to the branch.

During execution of an event stack, the operations defined in each crate are executed in the order that the crate list was passed.

<a name="AEN71306"></a>## OPTIONS



**-branch** *value*Specifies the branch index. Default is 0.

**-crates** *list*Specify a proper tcl list of crate modules to be operated on the branch.
	These crates must be compatible with the driver in use. Care should also
	be taken to ensure that the crate indices are all different.
	Default is an empty list.

<a name="AEN71321"></a>## EXAMPLES

<a name="AEN71323"></a>**Example 1. Sample setup of two camac crates on branch 0**

```
# define some camac crates
CBDCamacCrate create crate1 -crate 1
CBDCamacCrate create crate2 -crate 2

CBDCamacBranch create branch0 -branch 0
CBDCamacBranch config branch0 -crates [list crate1 crate2]
         
```

Defines two camac crates compatible with the CBD8210 branch driver and adds those to the camac branch, whose branch index is 0.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| delay | Up | CBDCamacCrate |
