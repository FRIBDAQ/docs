|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN101592"></a>waitForRing

<a name="AEN101596"></a>## Name

waitForRing -- Wait for a ring to exist with a timeout

<a name="AEN101599"></a>## Synopsis

```
package require ringutils

if {[waitForRing name timeoutsecs pollms ?host=localhost?]} {
    #   Ring came into being within timoutsecs seconds
} else {
    #  Timeout waiting for ring creation.
}
        
```

<a name="AEN101601"></a>## DESCRIPTION

Returns true if the ring `name` comes into existence on 
            `host` (which defaults to localhost) 
            within `timeoutsecs` seconds.  The ringmaster
            in `host` is polled every `pollms`
            milliseconds.  There will always be at least one poll for the ring regardless
            of the values of `timeoutsecs` or `pollms`

The operation throws an error if `host` does not exist or
            is not running a functional ring master daemon.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| ringExists | Up | containers |
