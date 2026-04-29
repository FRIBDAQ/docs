|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="mvlc3.devicecommand"></a>DeviceCommand

<a name="AEN105427"></a>## Name

DeviceCommand -- Base class for mvlcgenerate device commands

<a name="AEN105430"></a>## Synopsis

```
#include <mvlc/DeviceCommand.h>

class DeviceCommand : public CTCLObjectProcessor {

public:
    DeviceCommand(CTCLInterpreter& interp, const char* cmd, TCLConfigParser& parser);
    virtual ~DeviceCommand();
    virtual int operator()(CTCLInterpreter& interp, std::vector<CTCLObject>& objv);

protected:
    //
    virtual CReadoutModule* createDevice(std::string name) = 0; 
    TCLConfigParser& getParser() {return m_parser; }

};

        
```

<a name="AEN105432"></a>## DESCRIPTION

`DeviceCommand` provides an abstract base
            class that supports regisering the command to support creating, configuring
            and introspecting a device instance that is supported via a
            `CReadoutHardware` derived class.

The process of building a loadable extension to mvlcgenerate
            is described in tutorial detail in 
            [[x7385]].
            It will not be described here.

In summary, however, you define a derived class and implement
            `createDevice` that encapsulates the configuation
            and `CReadoutHardware` in a `CReadoutModule`
            and register that derived class with the command name you want, in the 
            interprter used  by mvlcgenerate to process configuration input files.

<a name="AEN105443"></a>## METHODS



`  DeviceCommand(CTCLInterpeter& interp, const char* cmd, TCLConfigParser& parser);`The contructor is invoked to register the command.
                            `interp` is the interpreter on which
                            the command will be registered.  `cmd`
                            is the command command's verb name.  Finally,
                            **parser** is the instance of the parser that
                            will process the configuration file.  This value can be gotten
                            via `TCLConfigParser::getInstance`

` CReadoutModule* createDevice(std::string name);`You will need to implement this method in your derived class.
                            The example in 
                            [[x7385]]
                            shows how to do this and what to put in your implementation.

<a name="AEN105476"></a>## SEE ALSO



- [[r105324]]

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CReadoutHardware | Up | CReadoutModule |
