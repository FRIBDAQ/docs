|  |  |  |
| --- | --- | --- |
| SpecTcl Programming Reference. |
| Prev |  | Next |


---

<a name="AEN24238"></a># V. SpecTcl Displays

<a name="AEN24240"></a># Introduction

The original SpecTcl only supported a single, hard coded visualization
      program, Xamine.  While Xamine is still supported, the internal support for
      visualizers has been generalized to provide the ability to extend SpecTcl
      to use other display programs.

The Spectra, root based display program was written and abandoned before
      gaining much traction because the CERN/Root team abandoned QTGsi and went in
      a much different GUI direction.  A Python/Qt based displayer using
      MatPltoLib is being developed and will live on top of these classes documented
      below.

**Table of Contents**[[r24244]] -- Display interface base class[[r24564]] -- Batch mode displayer[[r24577]] -- Displayer class for Xamine[[r24810]] -- Represent gates in Xamine[[r25142]] -- Describe a client button[[r25288]] -- Base class for button prompter descriptions[[r25304]] -- Prompter that does not prompt[[r25316]] -- Prompt for confirmation[[r25329]] -- Prompt for a text string[[r25341]] -- Prompt for a spectrum[[r25361]] -- Prompt for a filename.[[r25373]] -- Prompt for points[[r25388]] -- Encapsulate events from Xamine.[[r25419]] -- Encapsulate button press events[[r25540]] -- Manages displayers[[r25661]] -- Maintain a named set of display objects.[[r25768]] -- Associate display creators with display type names

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CPipelineEventProcessor |  | CDisplay |
