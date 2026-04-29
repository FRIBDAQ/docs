|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.ringutil"></a>getRingUsage

<a name="AEN106525"></a>## Name

getRingUsage -- Return list of ringbuffers and usage statistics

<a name="AEN106528"></a>## Synopsis

```
package require ringutils

getRingUsage ?host=localhost?
        
```

<a name="AEN106530"></a>## DESCRIPTION

Returns a list of the ringbuffers and usage statistics for all
            ringbuffers know to the optional `host` parameter.
            if `host` is omitted, it defaults to localhost

The return value is a list of one element per ringbuffer.  The elements themselves are 
            lists containing



1. Name of the ringbuffer.
2. A list of items that describe the ringbuffer and usage.  These are in order:
                   Size of the ringbuffer in bytes, the number of free bytes, max consumer count, 
                   the PID of the producder (or -1 if there is none), the number of bytes pending in
                   the consumer with the biggest backlog,  number of bytes pending in the consumer
                   that is most caught up, and lastly a list of client data.
   Each client data item is a pair (Tcl 2 item list), containing, in order,
                   the PID of the consumer and the number of bytes of backlog it has.

The proc throws an error if `host` does not exist or is
            not running a functioning ring master daemon.

<a name="AEN106545"></a>## EXAMPLE



```
package require ringutils
puts [getRingUsage]        
        
```


Might produce the output:

```
{OfflineEvbIn {8391008 8391007 100 -1 0 0 {}}} {__test__ {8391008 8391007 100 -1 0 0 {}}} 
{_mytestring_ {8391008 8391007 100 -1 0 0 {}}} {a {8391008 8391007 100 -1 0 0 {}}} 
{aa {8391008 8391007 100 -1 0 0 {}}} {blocking_326238 {8391008 8391007 100 -1 0 0 {}}} 
{difftest_326238 {8391008 8391007 100 -1 0 0 {}}} 
{duplicate_326238 {8391008 8391007 100 -1 0 0 {}}} {fox {8391008 8391007 100 -1 0 0 {}}} 
{infotest_326238 {8391008 8391007 100 -1 0 0 {}}} {isaring {2096896 2096895 10 -1 0 0 {}}}
 {mgrtest_326238 {8391008 8391007 100 -1 0 0 {}}} {remote_326238 {8391008 8391007 100 -1 0 0 {}}} 
 {ron {8391008 8391007 100 -1 0 0 {}}} {test {8391008 8391007 100 -1 0 0 {}}} 
            
```

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| TCL Ring package. | Up | ringExists |
