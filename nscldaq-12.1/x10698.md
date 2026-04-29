|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 39. Compatibility utilities | Next |


---

# <a name="AEN10698"></a>39.2. Writing event files with compatibilitylogger

The compatibilitylogger is a unix pipeline
            element that accepts old style NSCL buffers and produces an old
            style event file for a single run.  Normally this is the end stage of
            a pipline consisting of ringselector,
            compatibilitybuffer and itself used
            to write event files in old spectrodaq format.

Once an end of run event is seen, the event file is closed and
            the program exits.  Event files are segmented just as they are in
            both systems.  Event file segments are no larger than 2Gbytes. This
            allows them to be properly accessed over all versions of NFS.

Since the pipelines that use compatibilitylogger
            are intended to be used with the ReadoutShell,
            event filenames match those used by the ring buffer daq rather than
            those used by the spectrodaq system.
            This allows the ReadoutShell to properly
            maintain the file/directory structure of the stagearea.

Below is a sample pipeline that takes as input a ring buffer event file
            and produces the corresponing nscl buffer event file:

<a name="AEN10712"></a>**Example 39-3. Using compatibilitylogger to convert event files**

```
cd OldEventFiles
compatibilitybuffer <~/stagerea/complete/run-0123-00.evt | compatibilitylogger 
            
```

The example assumes the existence of a subdirectory
            OldEventFiles.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Compatibility utilities | Up | Converting NSCLDAQ-V10.x data to NSCLDAQ-11.x data |
