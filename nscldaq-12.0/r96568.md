|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="tcl3.loggerrestclient"></a>loggerrestclient

<a name="AEN96572"></a>## Name

loggerrestclient -- Client to Manager's Event Log REST Interface

<a name="AEN96575"></a>## Synopsis

```
package require loggerrestclient

LoggerRestClient name -host hostname -user username
name configure option value ?...?

name enableLogger logger-dest
name disableLogger logger-dest
set loggerInfo [name listLoggers]
name record recording-state
name isRecording
name start
name destroy
      
```

<a name="AEN96577"></a>## DESCRIPTION

Provides an object oriented interface to the part of the manager's
            REST server that controls event logging.  Each method of a
            `LoggerRestClient` instance makes a REST request of
            the server.  The request logic includes service discovery based
            on the current values of the `-host`, `-user`
            options and `clientutils::SERVICE` variables.

<a name="AEN96584"></a>## OPTIONS

Options control service lookup and how the server is connected during
         each method call.   As such the host, user and even the service can be
         varied from request to requrest.  Furthermore, the object is robust in
         the presence of server restarts that may change the actual server port.

The options described below must be properly defined prior to any
         method call that makes a REST request.



`-host`Host in which the server is running.

`-user`Username of the user that started th server.

<a name="AEN96599"></a>## METHODS

With the exception of the built in methods (e.g.
         `configure`, `cget`,
         `destroy`), each method call described
         below performs exactly one REST request.

The REST request includes service discovery which provides, from the
         Port Manager the port on which the server is listening for connection.
         This service discovery is performed for *every*
         REST request.



`enableLogger` `dest`Enables the logger whose log destination is
                  `dest`.  In the
                  `LoggerRestClient` API, loggers are
                  specified by their log destinations.  These are required by the
                  database APIs to be unique.

`disableLogger` `dest`Disables the logger whose log destination is
                  `dest`.

`listLoggers`Returns a list of dicts that describe the loggers known
                  to the server database.  Each list item is a dict that describes
                  a single logger and has the following key/value pairs:



idUnique integer number that is the logger's primary
                           database key.

daqrootThe root directory where the NSCLDAQ installation
                           lives.  Note that if the event logger runs containerized,
                           this path is expressed in terms of the filesystem
                           seen within the container.

ringThe URI of the ring buffer from which the logger
                           will log data.

hostThe host on which the event logger will run.

partialBoolean that is true if this is a partial event logger.

destinationThe directory (or top level directory if full event
                           logging is done) in which the event logging will be
                           done.  If the event logger runs containerized,
                           this destination will be a path in the containerized
                           environment.

criticalBoolean that is true if the logger is critical to the
                           functioning of the experiment.  If this is true
                           and the logger exits prematurely for any reason,
                           the manager forces a SHUTDOWN
                           transition.

enabledBoolean that is true if the event logger is enabled
                           to record data.

containerIf the event logger should run containerized, this is
                           the name of the container in which it will run.  If
                           the event log runs in the native environment,
                           this will be an empty string.

`record` `state`Set the
                  global recording state to `state`.  This
                  should be a boolean that is true to enable global recording
                  or false to disable it.

`isRecording`Returns a boolean value.  The value will be true if event recording
                  is enabled or false if not.

`start`Starts the appropriate set of loggers.  For a logger to start,
                  it must be enabled and the global recording flag must also
                  be true.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| kvclient | Up | ReadoutRESTClient |
