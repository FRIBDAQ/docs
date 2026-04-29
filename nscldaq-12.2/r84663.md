|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="AEN84663"></a>Program

<a name="AEN84667"></a>## Name

Program -- Provide access to the Program part of FRIB managed experiment definition database

<a name="AEN84670"></a>## Synopsis

```
from nscldaq.mg_database import Program

def __init__(self, db)...
def exists(self, name)...
def add(self, name, path, host, container, wd, options)...
def delete(self, name)...
def list(self)...
def types(self)...
      
```

<a name="AEN84672"></a>## DESCRIPTION

Programs in the FRIB managed experiment environment represent executable code or scripts
         that can be run as part of a sequence that is attached to a data acquisition system state
         transition.  For example,  When the system boots up initially, sequences associated With
         that state transition are run.  Those  sequences contain lists of programs to activate.

Each program has a unique name and several other properties, such as the 
         executable/script to run, the host and container in which to run it and the
         environment in effect when the program runs.

Programs also have a property that expresses how they are expected to run.  This is called the
         program's *type*.  Some programs, like a readout are considered
         *Critical*, which means that if they exit, the system is brought down and
         will need to be rebooted to start again.  Others are *Persistent*
         meaning they are intended to live frome when they were started until the experiment is 
         shutdown.  Persistent programs are not critical so, if they exit, this fact is noted but
         the experiment is allowed to continue to run.  Finally, there are *Transitory*
         programs.  These are expected to run for a finite duration and then exit.  Typically they perform
         a single operation and exit.  For example, Readout's run ReST servers.  When a transition is performed
         to the BEGIN state, a transitory program will run to tell each Readout to start data taking.

<a name="AEN84681"></a>## METHODS



def init(self, db)
            Called when a `Program` is constructed.  
               The `db` is an sqlite3 connection object that
               is connected to the FRIB managed experiment configuration/database file.
               See 
               [https://docs.python.org/3/library/sqlite3.html](https://docs.python.org/3/library/sqlite3.html) 
               for information about how to construct a connection object.

def exists(self, name)
            Returns True if the program named `name`
               has been defined.

def add(self, name, path, host, container, wd, options)
            Attempts to add a new program  definition to the configuration.  
               `name` is  the name associated with the program.
               `name` must be unique or else 
               a `ValueError` will be raised.

`path` is the file system path to an executable
                  file that will be run when the program is run.  This path must exist
                  within the context of the container in which the program is specified to run.
                  `host` is the host in which the program will run and
                  `container` is the name of the container definition that
                  specifies the container in which the program will be run.
                  `wd` specifies the working directory in which the program
                  is started. Note this, as well is interpreted in the context of the container.

`options` specifies a set additional program options.  These
                  options are not mandatory.  The options are specified as a dict.  The following
                  keys are recognized (others are silently ignored):
                  type The program type.  This can be one of 
                  Transitory, Critical or Persistent.
                  initscript  specifies the path (in the context of the running program) to
                  a script that will be run prior to execution of the program.   The script will be executed in the
                  context of the host and container in which the program is run.  The contents of the script will
                  be pulled into the database.
                  options is an iterable of the program options passed to the program on startup.
                  The elements of this list are either pairs or single values.  Pairs are options and their values.  singal
                  values are just options.  For example [('--ring', 'fox'), (--debug,)].
                  parameters are an iterable.  Each item of the iterable is a parameter passed to the
                  program as it starts.  For example ['/user/fox/configuration.txt', 'output-file']
environment specifies additional environment variables that are defined prior to running
                  the program.  THe format of this value is the same as for options for 
                  example: [('DAQROOT', '12.1-003'), ('ENABLE_DEBUG', )]

def delete(self, name)
            Attempts to delete the program with the name `name`. If there is no
               program by that name, `ValueError` is raised.

def list(self)
            Lists all programs and their properties.  The return value is a list of dicts.
               Each dict describes one program and has the following keys:

id  the primary key of the root table entry describing the protgram.
                  name the name given to the program.
                  path path to the executable or script file that will be run.  This 
                  shouild be interpreted in the context of the container in which the program is started.
                  host  the host in which the program is run.
                  wd the working directory in which the program is started.  This should be
                  interpreted in the context of the container in which the program will be started.
                  containerThe name of the container in which the program will be run.  This
                  is the name of a container definition in the configuration database, not a container image name.

In addition, the more key contains, as a value, most of the options:
               type is a string identifying the program type e.g. Transitory.
               options is a list of prorgram options.
               parameters is a list of program  parameters.
               environment is a list of environment definitions.
               Finally, initscript_contents are the contents of the initialization
               script, or an empty string if one was not specified when the program was defined.

def types(self)
            Returns a list of the legal program types.  At the time this is being written, th is is
               ['Critical', 'Persistent', 'Transitory']

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| EventLog | Up | LogBook |
