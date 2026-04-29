|  |  |  |
| --- | --- | --- |
| SpecTcl Programming Reference. |
| Prev |  | Next |


---

# <a name="AEN24993"></a>CXamineButtonPrompt

<a name="AEN24997"></a>## Name

CXamineButtonPrompt -- Base class for button prompter descriptions

<a name="AEN25000"></a>## Synopsis

```
#include <XamineButtonPrompt.h>

class CXamineButtonPrompt      
{
  
public:

  CXamineButtonPrompt (const std::string& am_sPromptString  );
  CXamineButtonPrompt(const char* pPrompt);
  

  std::string getPromptString() const;
 
  virtual   void FormatPrompterBlock(ButtonDescription& rButton) const   = 0;
};

        
```

<a name="AEN25002"></a>## DESCRIPTION

`CXamineButtonPrompt` is an abstract base
            class that's used to describe prompting that Xamine must do
            prior to dispatching a button event to the client.
            The prompter is specified as part of the button definition
            message sent to Xamine.  Prompters have a string associated
            with them, and this string is maintained by this base class.

The point of this class hierarchy is to provide the
            `FormatPrompterBlock` method
            interface definition.  In concrete subclasses, this method
            is expected to fill in the part of a
            ButtonDescription structure that pertains
            to describing the button prompter.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| XamineButton | Up | CXamineNoPrompt |
