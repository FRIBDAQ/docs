|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="ccusb3-LeCroy2551"></a>LeCroy2551

<a name="AEN44697"></a>## Name

LeCroy2551 -- control a LeCroy 2551 Scaler

<a name="AEN44700"></a>## Synopsis

**LeCroy2551 create *name base*
**

**LeCroy2551 config *name option value ...*
**

**LeCroy2551 cget *name*
**

<a name="AEN44710"></a>## DESCRIPTION

The LeCroy2551 is intended to control a LeCroy 2551 scaler situated on a crate controlled by a CC-USB. It is the counterpart to the CBDLeCroy4434 driver that lives in the VMUSBReadout framework. In this case, the LeCroy2551 can be registered directly to a stack and does not need to be registered first to a CamacCrate. There is no reason you cannot register it to a CamacCrate though.

During initialization, all scalers are cleared.

At the end of the run, no actions are taken.

During stack execution initiated by an event trigger, all 12 scaler channels are read individually.

<a name="AEN44716"></a>## OPTIONS



**-slot** *value*Specifies the slot of the CAMAC crate the target module is occupying. Default is 1.

<a name="AEN44725"></a>## EXAMPLES

<a name="AEN44727"></a>**Example 1. A simple setup of a single scaler**

```
LeCroy2551 create sclr -slot 10
         
```

Sets up a LeCroy 2551 scaler module in slot 10.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| LeCroy4434 | Up | ULMTrigger |
