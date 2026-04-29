|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

<a name="AEN3711"></a># VI. frameworks

**Table of Contents**51. [[c3713]]51.1. [[c3713#AEN3728]]51.2. [[x3733]]51.3. [[x3744]]51.4. [[x3810]]52. [[c3879]]52.1. [[c3879#AEN3899]]52.1.1. [[c3879#AEN3950]]52.2. [[x4067]]52.3. [[x4112]]52.4. [[x4145]]52.4.1. [[x4145#sec_tsextractors]]53. [[c4231]]53.1. [[c4231#AEN4241]]53.2. [[x4248]][[f4252]][[r4255]] -- Start the event builder pipeline.[[r4320]] -- Stop the event builder pipeline.[[r4333]] -- Reset timestamp history[[r4347]] -- Flush event builder event queues.[[r4360]] -- Start a ring fragment source for the event builder.[[r4406]] -- Start S800 data source[[f4424]][[r4430]] -- Initialize the EZBuilder layer.[[r4483]] -- EZBuilder begin run actions[[r4502]] -- EZBuilder end run actions.[[r4516]] -- Event builder cilent framework[[r4560]] -- Submit event fragments.[[r4579]] -- Event builder input statistics[[r4627]] -- Get orderer output statistics[[r4646]] -- Get the late fragment statistics.[[r4674]] -- Bind scripts to data late events.[[r4698]] -- Supply a script to invoke on barrier events.[[r4718]] -- Create event source queues.[[r4736]] -- Mark a data source dead.[[r4751]] -- Revive all dead data sources associated with a socket[[r4766]] -- Empty all input queues.[[r4779]] -- Reset timestamp clocks.54. [[c4792]]54.1. [[c4792#AEN4803]]54.2. [[x5095]]54.3. [[x5110]]54.4. [[x5182]]54.5. [[x5198]]54.6. [[x5208]]55. [[c5213]]55.1. [[c5213#AEN5237]]55.2. [[x5253]]55.3. [[x5294]]55.3.1. [[x5294#AEN5320]]55.3.2. [[x5294#AEN5355]]55.3.3. [[x5294#AEN5388]]55.3.4. [[x5294#AEN5415]]55.4. [[x5455]]55.4.1. [[x5455#AEN5459]]55.4.2. [[x5455#AEN5487]]55.4.3. [[x5455#AEN5588]]55.4.4. [[x5455#ccusb-general-tcldriver-usage]]55.5. [[x5713]]55.6. [[x5726]]56. [[c5775]]56.1. [[c5775#AEN5801]]56.2. [[x5817]]56.3. [[x5848]]56.3.1. [[x5848#AEN5879]]56.3.2. [[x5848#AEN5910]]56.3.3. [[x5848#AEN5935]]56.3.4. [[x5848#AEN5960]]56.4. [[x6022]]56.4.1. [[x6022#AEN6042]]56.4.2. [[x6022#AEN6133]]56.4.3. [[x6022#AEN6225]]56.5. [[x6256]]56.5.1. [[x6256#AEN6273]]56.6. [[x6297]]56.6.1. [[x6297#AEN6312]]56.7. [[x6339]]

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Service Port Manager. |  | Event orderer and its user interface |
