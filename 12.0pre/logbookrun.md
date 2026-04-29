|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="py3.run"></a>LogBook.Run

<a name="AEN71838"></a>## Name

LogBook.Run, LogBook.Transition -- Encapsulate runs and their transitions for Python

<a name="AEN71842"></a>## Synopsis

```
PYTHONPATH=$DAQROOT/pythonLibs/nscldaq python3

import LogBook.LogBook as LogBook
...
book = LogBook.LogBook('logbookfile.log')
run  = LogBook.find_run(1)
      
```

```
id     = run.id
number = run.number
title  = run.title

      
```

```
n   = run.transition_count()
tnum = 0
begin_run = run.get_transition(tnum)
if run.is_current():
     #  Run is the current/active run
     
last_transitionid = run.last_transitionid()
last_text         = run.last_transition()

if run.is_active():
      # Run is still active.

run.end([remark])
run.pause([remark])
run.resume([remark])
run.emergency_end([remark])

      
```

```

id             = transition.id
transitionid   = transition.transition
transitiontext = transition.transition_name
timestamp      = transition.time
comment        = transition.comment
shift          = transition.shift

      
```

<a name="AEN71848"></a>## DESCRIPTION

This page describes two classes:
            `LogBook.Run` which encapsulates a run and
            the associated `LogBook.Transition` which
            encapsulates a single run state transition.

<a name="AEN71853"></a>## LogBook.Run

This section desccribes the `LogBook.Run`
         class which provides readonly attributes
         and methods to access and modify runs.

<a name="AEN71857"></a>### Attributes



Integer` id`Contains the run's primary key.

Integer` number`Provides the run number.  This differs from the primary key
                     because some experimenters assign skip run numbers for
                     organizational purposes.

String` title`Provides the run title string.

<a name="AEN71878"></a>### METHODS



` Integer transition_count();`Returns the number of transitions the run has undergone.

` LogBook.Transition get_transition(Number n);`Returns a `LogBook.Transition`
                     object that encapsulates transition number
                     `n` numbered from zero.
                     If `n` is out of range
                     `LogBook.error` is raised.

` Boolean is_current();`Returns True if this object is the
                     current run.

` Boolean is_active();`Given the constraints enforced by the database
                     API, this is equivalent to `is_current`
                     because the API enforces that there only be one active
                     run at a time and that it is the current one.

` Integer last_transitionid();`Returns the numerical value that specifies the last
                     transition.

` String last_transition();`Returns the transition name string of the last transition.

` LogBook.Run end(optional String remark);`Logs an end run for the run.  If provided
                     `remark` is a text string that
                     is logged along with the transition.  The return value of
                     this method is the run being operated on, this supports
                     Chaining like

<a name="AEN71949"></a>```
print(run.end('end run example').title + ' ended just now')
                   
```

` LogBook.Run pause(optional String remark);`Pauses the run. If `remark`
                     is provided it is a text string that's loggeda long
                     with the pause transition. The return value is the
                     run itself to support chaining.  See the example in
                     `end`

` LogBook.Run resume(optional String remark);`Logs a pause run with the optional `remark`
                     string. The return value is the run being resumed.

` LogBook.Run emergency_end(optional String remark);`Logs an emergency end of run for the run with the optional
                     remark string `remark`.
                     The retrun value is the run operated on.

<a name="AEN71988"></a>## LogBook.Transition

Transitions (`LogBook.Transition` objects)
         are fetched from a `LogBook.Run`
         object via the `get_transition` method.
         These have no methods but support the following read-only attributes:



Integer ` id`Primary key of the transition

Integer` transition`Integer code that defines the transition.

String` transition_name`Human readable string that defines the transition.

int` time`Timestamp that can be passed to e.g.
                  `datetime.fromtimestamp`.

String` comment`Comment associated with the transition.

LogBook.Shift` shift`Returns a `LogBook.Shift` object
                  that wraps the shift that was on-duty at the time the
                  transition was logged.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| LogBook.Shift | Up | LogBook.Note |
