|  |  |  |
| --- | --- | --- |
| SpecTcl Programming Reference. |
| Prev |  | Next |


---

<a name="AEN23943"></a># V. SpecTcl Displays

<a name="AEN23945"></a># Introduction

The original SpecTcl only supported a single, hard coded visualization
      program, Xamine.  While Xamine is still supported, the internal support for
      visualizers has been generalized to provide the ability to extend SpecTcl
      to use other display programs.

The Spectra, root based display program was written and abandoned before
      gaining much traction because the CERN/Root team abandoned QTGsi and went in
      a much different GUI direction.  A Python/Qt based displayer using
      MatPltoLib is being developed and will live on top of these classes documented
      below.

**Table of Contents**[[r23949]] -- Display interface base class[[r24269]] -- Batch mode displayer[[r24282]] -- Displayer class for Xamine[[r24515]] -- Represent gates in Xamine[[r24847]] -- Describe a client button[[r24993]] -- Base class for button prompter descriptions[[r25009]] -- Prompter that does not prompt[[r25021]] -- Prompt for confirmation[[r25034]] -- Prompt for a text string[[r25046]] -- Prompt for a spectrum[[r25066]] -- Prompt for a filename.[[r25078]] -- Prompt for points[[r25093]] -- Encapsulate events from Xamine.[[r25124]] -- Encapsulate button press events[[r25245]] -- Manages displayers[[r25366]] -- Maintain a named set of display objects.[[r25473]] -- Associate display creators with display type names

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CPipelineEventProcessor |  | CDisplay |
