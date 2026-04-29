|  |  |  |
| --- | --- | --- |
| mpiSpecTcl. |
| Prev |  | Next |


---

# <a name="AEN948"></a>CMPITclCommand

<a name="AEN952"></a>## Name

CMPITclCommand -- Jacket a command that runs in other ranks

<a name="AEN955"></a>## Synopsis

```
#include <MPITclComamnd.h>

class CMPITclCommand : public CTCLObjectProcessor {
public:
    CMPITclCommand(CTCLInterpreter& interp, const char* command, CTCLObjectProcessor* pActual);
protected:
    int operator()(CTCLInterpreter& interp, std::vector<CTCLObject>& objv);

};          
                    
```

<a name="AEN957"></a>## DESCRIPTION

This wrapper when registered in all processes, and the command registered
                        is to be executed in the root process executes the encapsulat4ed 
                        command in all of
                        the non-root processes. The command is *not*
                        executed in the root process.



**METHODS**

`  CMPITclCommand(CTCLInterpreter& interp, const char* command, CTCLObjectProcessor* pActual);`Wraps the command implemented by `pActual`
                                so that it is executed in all but the root rank when the root interpreter
                                executes the `command` command on the 
                                `interp` interpreter.  In the remote processes, the
                                command will be executed in that process's main thread's interpreter.

` int operator()(CTCLInterpreter& interp, std::vector<CTCLObject>&*amp; objv);`This function is called when the command specified in the constructor is
                                executed by the interpreter specified in the constructor.  That interpreter
                                is passed as the `interp` parameter. `objv`
                                are the command words.  `objv[0]` is the command name which,
                                normally, is the value of `command` passed to the constructor.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CMPITclCommandAll | Up | CMPITclPackagedCommandAll |
