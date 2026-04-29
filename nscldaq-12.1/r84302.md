|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="python3.nscldaqutils"></a>nscldaqutils

<a name="AEN84306"></a>## Name

nscldaqutils -- Provide a set of utilities for NSCLDAQ

<a name="AEN84309"></a>## Synopsis

```
from nscldaq.nscldaqutils import ssh, getSshOutput, getSshError

result = ssh(ahost, acommand)
print(f'Output from {acommand}@{ahost} ', getSshOutput(result))
print(f'Error from {acommand}@{ahost}', getSshError(result))

from nscldaq.nscldaqutiles import RingMaster
import pprint

rm = RingMaster(ahost)
print("Ring usage from ", rm.host())
pprint.pp(rm.list_rings())

        
```

<a name="AEN84311"></a>## DESCRIPTION

Some two useful sets of utilities are provided:



1. The ability to execute commands in a remote host via
                       ssh.
2. The ablity to obtain information about ringbuffer usage in
                       a local or remote host.


<a name="AEN84319"></a>### ssH, getSshOuptut, getSshError

The ssh method takes two parameters, a hostname and a command
                string.  THe method attempts to execute the command in the
                (remote) host and caputures both the stderr and stdtout from
                that process.

The software tries to re-establish the environment in the local
                system in the remote system.  This includes:



- If necessary, rebuilding the container environment in the
                          remote system.
- Copying all environment variabes to the remote system
- Establishing the same curretn working directory.


This all assumes the remote system shares the host
                file-system, or that the remote system at  least has a similar
                directory tree structure.

To reconstruct the container environment two environment
                variables must be defined:



APPTAINER_CONTAINERMust point to the full path of the container image in the
                        target system's host.  Note that for later versions of
                        apptainer, this is established in the localhost automatically
                        when the container is started.  This is not the case for 
                        **singularity**

CONTAINER_BINDINGSMust contain a vaild value for the singularity/apptainer
                        `--bind` option that will construct the
                        desired bindings in the target.

The command returns a two element list.  The first element is the complete 
                standard output from the operation while the second the complete 
                standard error.  Note that this inlcudes output and error from the process
                of setablishing the environment in the remote system.
                Therefore, a marker is inserted into both of these just prior to
                executing the command.

Passing the result to **getSshOutput** will
                analyze the stdout from the ssh operation and return a list
                of the lines output by the desired command.  Similarly,
                **getSshError**, when passed the result will
                return the list of  stderr lines (if any) from the command.

<a name="AEN84349"></a>### The RingMaster class

Allows python programs to interact with the ringmaster in the 
                local or remote systems to obtain ring usage information.
                The constructor of the class takes a single parameter, The
                name of the host whose ring master we want to communicate with.
                The method `list_rings` then produces the ring usage
                for that host.  The method `host`
                returns the host on which the object was constructed.

The result of the `list_rings` method
                returns a list.  Each list element describes a ringbuffer and its
                usage as a dict.

The dicts have the following keys:



nameThe name of a ringbuffer.

sizeSize of the ringbuffer in kbytes.

freeNumber of kbytes free in the ring buffer.  This
                        is the size of the largest put that could be made into the ringbuffer
                        without blocking.

maxconsumersMaximum number of consumers the ringbuffer has been configured for.

producer_pidProcess id of the producer.   If this is -1 
                        the ringbuffer does not have a producer.

maxgetThis is the largest consumer backlog.  The name comes from the fact
                        that this is the largest get that could be made by any consumer.

mingetThe smallest consumer backlog.

consumersThe list (possibly empty) of consumers for the ringbuffer.
                        Each list element is a two element dict that contains
                        the keys consumer_pid and backlog

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| pidtocommand | Up | 3vmusb |
