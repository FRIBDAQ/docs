|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.chanlog"></a>chanlog

<a name="AEN8205"></a>## Name

chanlog -- Write a set of channels to file

<a name="AEN8208"></a>## Synopsis

**chanlog *channelfile* *outfile*
**

<a name="AEN8213"></a>## DESCRIPTION

Logs  the  names, values and units of a set of EPICS channels to file.  In the
       command invocation,
       *channelfile*
       is a file that contains the names of the channels
       to  lookup and log.  If
       *channelfile* is
        -, then the channels are taken from stdin.
       *outfile*
       is the name of a file to which the channels will be logged.  If
       *outfile*
       is -, the output is sent to stdout.

The  channel  file  is  an ordinary text file that contains the names of EPICS
       channels, each channel is separated by whitespace (note that a newline  counts
       as  whitespace).   No  comments  are allowed, in contrast to the form of input
       file expected by e.g. epicsdisplay.  The following is a sample input file:

```
       Z001DV Z002DH
       Z003DV
       Z004QA

       Z012QB
        
```

This file will output the values and units for  5  channels:
       Z001DV,  Z002DH,
       Z003DV, Z004QA and Z004QA.

Output will consist of a line of text for each channel in the input
           file.  Each line will consist of a set of white-space separated 
	   components.  The first component is the name of  a channel followed
           by a colon.  The second element is the channel value.
	   The final element is the channel engineering units.

If the value of a channel cannot be gotten, the remainder of the
	   line following the channel name will be the error message
	   generated for that channel for example:
	   Z001DH: ca_pend_io failed User specified timeout on IO
        operation expired.

<a name="AEN8230"></a>## EXAMPLES

All of the examples assume that a file named 
	  channels.txt has been created
	  that contains the set of channel names of interest, and that 
	  chanlog is in your path.

<a name="AEN8235"></a>**Example 1. Viewing a set of channel values interactively**

```
chanlog channels.txt -
	  
```

<a name="AEN8238"></a>**Example 2. Writing a set of channels to a file**

```
chanlog channels.txt somefile.out
          
```

<a name="AEN8241"></a>**Example 3. Appending a set of channels to a file**

```
chanlog channels.txt - >>somefile.out
           
```

<a name="AEN8244"></a>**Example 4. Piping a set of channels to a program for processing**

```
chanlog channels.txt - | someprogram
           
```

<a name="AEN8247"></a>## DEPENDENCIES





- Epics software must be installed and located by the installer
- The Epics utility caRepeater should
                  be in your path.  This is in the architecture specific 
  		bin directory of the Epics installation.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| 1epics | Up | controlpush |
