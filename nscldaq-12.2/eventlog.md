|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN84533"></a>EventLog

<a name="AEN84537"></a>## Name

EventLog -- Python3 API for the Eventlogger part of the managed expeiment configuration file database.

<a name="AEN84540"></a>## Synopsis

```
from nscldaq.mg_database import EventLog

class EventLog:
   def __init__(self, handle)...
   def exists(self, destination)...
   def add(self, root, source_uri, destination, container, host, options)...
   def info(self, destination)...
   def list(self)...
   def delete(self, id)...
   def enable(self, id)...
   def disable(self, id)...
   def enable_all(self)...
   def disable_all(self)...
   def start_recording(self)...
   def stop_recording(self)...
   def is_recording(self)...
      
```

<a name="AEN84542"></a>## DESCRIPTION

This class provides access to the tables in the FRIB managed experiment system that
         describe how to log data to disk.  The system recognizes two types of event loggers that,
         for lack of better terminology are called *full* and 
         *partial*.   These determin how the destination fo the logger
         is used.  It may be worth reviewing the file system structure used by the event logger
         for the **ReadoutShell**

A partial logger simply writes event files into the destination directory.  This is analagous
      to how the multilogger for **ReadoutShell** operates.
      A full logger maintains the directory struture the main event logger for
      **ReadoutShell** maintains, rooted in its destination directory.

Event loggers are identified by their destination, which must be unqique, and an identifying
         integer, which is the primary key of the logger in the root table that descsribes event loggers.

Event loggers can be *enabled* or *disabled*.
         Disabled event loggers don't  record data.  Additionally, there is a global 
         recording  flag which, when True means that when a run
         begins, event loggers that are enabled are started to record data.

<a name="AEN84557"></a>## METHODS



def __init__(self, handle)
            Called when constructing an `EventLog` object.  The
               `handle` parameter is the sqlite3 database 
               connection object that is
               connecte4d to the configuration database file being manipulated.
               See
               [https://docs.python.org/3/library/sqlite3.html](https://docs.python.org/3/library/sqlite3.html) 
               for information about how to construct a connection object.

def exists(self, destination)
            Returns True if an event logger is already defined
               that writes to the specific `destination` directory.

def add(self, root, source_uri, destination, container, host, options)
            Attempts to add a new event logger to the configuration database.
               The `root` specifies the top level directory of the
               version of NSCLDAQ whose event logger will be used to log data.
               `source_uri` specifies the URI of the ring buffer
               from which cata will be logged.  `destination`
               is the directory into which data wil be logged.  There must not
               be a logger defined with the same destination or a `ValueError`
               will be raised.  The destination must be a valid directory path in the 
               container.

`container` specifies the name of the container in which the
               logger will be run and `host` specifies the host in which the
               logger will run.

`options` is a dict that specifies additional options. The keys
               that are recognized (unrecognized keys are ignored) are:
               partial whose value must be a boolean.  True
               means the logger will be partial if omitted or False the logger
               will be a full logger.  critical whose value must be a boolean.
               If True then an unexpected event log exit will stop the experiment
               making it necessary to reboot the experiment after the problem has been fixed.  If 
               False  the experiment continues to run after an unexpected eventlog
               exit.  The default, if not supplied is True.
               enabled if supplied must also take a boolean value.  IF this
               value is true, then the event logger is enabled to record data the next time event data
               would be logged. This is True by default.

On success, the id of the logger is returned.

def info(self, destination)
            Returns information about the logger which is defined with the
               `destination`.  The information is returned as a dict
               with the following keys:

The keys in the dict are:
               id is the id of the logger.  This is the value returned from 
               the `add` method.
               root is the root directory for the version of NSCLDAQ whose 
               **eventlog** program is run to log data.
               ring is the URI of the ringbuffer whose data are analyzed.
               host is the name of the host in which the logger will run.
               partial is True if this is a partial logger.
               destination is the destination of the logger.
               critical  True if the logger is a critical logger.
               container Is the container in which the **eventlog**
               is run.

def list(self)            
            Returns a list of dicts, one for each defined loggers.  The contents of each dict
               is identical to that described for `info`.

def delete(self, id)
            Deletes the event logger with `id` as the id returned from
               e.g. `add` or
               `info`. If there is no corresponding logger, 
               `ValueError` is raised.

def enable(self, id):
            Enables the logger with the id `id`
               This means that the next time a recorded run is started, this logger will
               be started.  Note that `ValueError` is raised if there is
               no matching logger.

 def disable(self, id)           
            Disables the logger identified by `id`

def start_recording(self)
            Sets the global recoring flag to True.
               The next begin run, will start all enabled event loggers to log event data
               to their destinations.  Eventloggers are started with the `--oneshot`
               so they will log a single run and exit.

def stop_recording(self)
            Sets the global recording flag to False
               The next begin run will not start any event loggers.

def is_recording(self)
            Returns the state of the global recording flag.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Container | Up | Program |
