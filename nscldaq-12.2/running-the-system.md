|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 15. Simple V775 readout | Next |


---

# <a name="AEN9390"></a>15.5. Running the system.

In this section we are going to run the Readout software with
           a Readout GUI front end that can manage recording the event data.
           This mode also supports running the Readout program on a remote system.
           We will also take you on a brief tour of the way the directories
           for recorded data are organized.

To prepare for this we will need to:



- Set our account up for password-less login over ssh within
                      the lab.
- Designate a directory tree for event recording and create
                      a symbolic link that points to it.

## <a name="AEN9399"></a>15.5.1. Readout GUI

The Readout GUI runs your readout program over an ssh pipe.
                This allows it to start Readout in any system that shares
                the directory in which your Readout is located.  For
                experimental accounts, this is any system within the building,
                though clearly you need to run Readout on the system that
                is attached to the hardware it must access.

This is normally used in production experiments where users are
                located in the data U's but their Readout will run on
                spdaq systems in a vault.

In order to run the Readout program over an ssh pipe, you need
                to first set up your account so that you don't need to provide
                a password when ssh-ing from linux system to linux system within
                the lab.  This involves creating an authentication key for you
                as a user, without a passphrase and installing the public
                key as an authorized key:

<a name="AEN9404"></a>**Example 15-17. Setting up ssh for password-less login**

```
ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (/home/a/.ssh/id_rsa):Enter
Created directory '/home/a/.ssh'.
Enter passphrase (empty for no passphrase):Enter
Enter same passphrase again: Enter
Your identification has been saved in /home/a/.ssh/id_rsa.
Your public key has been saved in /home/a/.ssh/id_rsa.pub.
The key fingerprint is:
3e:4f:05:79:3a:9f:96:7c:3b:ad:e9:58:37:bc:37:e4    


                
```

In the example above, **Enter** means to use
                the Enter key
                on your keyboard.  Note that some of the output may be slightly different
                than what you see.

Next you must add the public key file (~/.ssh/id_rsa.pub)
                to the list of keys that are considered known authentication key:

<a name="AEN9418"></a>```
cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
                
```

This command appends your public key to the authorized keys list
                creating it if necessary.

Next you need to be sure the directory tree from your home
                directory down into .ssh has permissions
                set properly.

<a name="AEN9423"></a>```
chmod g-w,o-w ~
chmod 0700 ~/.ssh
                
```

These permissions ensure that only you can modify
                    the permissions of the
                    .ssh directory and that only
                    you can see the contents of that directory.  These
                    permissions revent other people from stealing the private
                    half of your key pair, which would allow them to impersonate
                    you.

If you do not set up the permissions to protect your
                    private key, ssh will refuse to let you use the key pair
                    to do password-less logins.

## <a name="AEN9428"></a>15.5.2. Creating a directory in which to record events

Where you put events depends on the type of account you have
                and the volume of the data you intend to record:



- If you have an account for a specific experiment, prior to
                      the experiment an event area will be allocated and
                      assigned to your account.
- If you have a test account and have told the helproom
                      that you will need to record and retain a large amount
                      of event data during your tests, your account will be
                      assigned  a test event area.
- If you have a test account and don't need to record
                      much data you can record it in a directory in your
                      home diretory tree.

We will assume that you only need to record a small
                amount of data and that you will create a
                directory in which to record data data:

<a name="AEN9439"></a>**Example 15-18. Creating an event area for a small amount of data**

```
mkdir ~/events
ln -s ~/events ~/stagearea
                
```

The first command creates the directory in which you will record
                your data. The second, creates a symbolic link expected by
                the Readout GUI.

## <a name="AEN9443"></a>15.5.3. Running and configuring the ReadoutGUI

Now that we have prepared the account we can start the
                Readout GUI:

<a name="AEN9446"></a>```
$DAQBIN/ReadoutShell
                
```

The Readout GUI can manage several Readout programs that
                contribute data to an *Event Builder*.
                The Readout GUI refers to these programs as
                *Data Sources*.  The first time you
                start the Readout GUI you must specify the set of data
                sources it manages.

ReadoutGUI stores its state in the event area.  If you
                restart ReadoutGUI with the same event area it will remember
                the data sources you selected.

To set up your data source, click the
                Data SourceAdd...
                menu entry.  In the resulting popup dialog select SSHPipe
                from the listbox and click Ok.

Each data source type is parameterized in a manner
                appropriate to its type.  In our case, the parameters
                we need to fill in in the resulting dialog box are:



Host name:The name of the computer in which Readout
                            will run.  If Readout will run in the
                            computer on which ReadoutGUI is running,
                            you can leave the default as
                            localhost.

Readout program:Use the Browse...
                            button to locat your Readout program
                            and select it.

Once you have selected the appropriate parameterization
                for the SSHPipe data source
                type to run your Readut, Click Ok.

Before acquiring data, you must start the data
                source(s).  Click the Start
                button to do this.

When the Readout program starts successfully, you can
                click the Begin button to
                start a run and End button
                to end the run (Begin becomes
                the End button when a run is
                active).

To record a run to disk, check the
                Record checkbutton
                before starting the run.

Record a few short runs before continuing to the next
                section

### <a name="AEN9484"></a>15.5.3.1. A brief tour of the event area structure

The event area maintains a structure that allows
                    non event data to be associated with event files.
                    The mechanics of doing that are beyond the scope
                    of this (already too long) tutorial.  For the sake
                    of this section, it's only important to know that
                    the event area uses symbolic links to provide two
                    views of the data.

The event file view provides a single directory
                    which appears to have all event files (appears
                    because in reality this directory contains
                    only symbolic links to the actual event
                    files).

The directory
                    ~/stagearea/complete contains
                    the event file view.  When analyzing data
                    offline this is usually the directory you will need
                    to see.
                    For experiments that don't store metadata with runs,
                    this is usually the only directory you need to look at

The Run view provides a view of the data in which
                    all of the data associated with each run is in its
                    own directory.  The
                    ~stagearea/experiment directory
                    provides this view.

Within this view you will find a directory for each
                    run that was recorded to disk.  If you have not
                    assocated metadata with runs, these directories
                    will only contain the event files for that run,
                    e.g. ~/stagearea/experiment/run1
                    will contain
                    run-0001-00.evt.

If you have associated metadata with the runs, the
                    metadata at the time each run ends is also stored
                    in that run's directory.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Creating the tailored SpecTcl | Up | Taking the example further. |
