|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 30. Sequencing runs | Next |


---

# <a name="AEN7939"></a>30.2. Using the sequencer.

The sequencer GUI consists of a table called the
	   *run plan table* Edit this
	   table to set the parameters for each action item
           column for each run in the plan (runs are rows across
	   the table).

The
	   File->Save...
	   menu will save a run plan for later use.  If you've already created
	   a run plan, you can read it in with the
	   File->Open...	   
	   menu selection.
	   Finally the
	   File->Clear
	   menu selection clears the run plan table.

The length of each run is set by the length of the timed run section
	  on the main ReadoutGUI window.  To execute a run plan, 
	  click the Execute button on the 
	  run plan table window.  This button then is relabeled
	  Abort, and can be used to abort
	  a run plan if something goes wrong.

As the run plan executes, the run that is active is highlighted on
           the run plan table.
           When the run plan is complete, or if the run plan was
	   aborted,  the 
	   Abort is relabeled
	   Execute and will restart the
	   run plan if clicked.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Sequencing runs | Up | Theringselectorapplication |
