|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.CTCLTimer"></a>CTCLTimer

<a name="AEN44928"></a>## Name

CTCLTimer -- 
            Abstract base class for C++ objects attached to timer events.

<a name="AEN44931"></a>## Synopsis

```
#include <TCLTimer.h>
...
class CTCLTimer  : public CTCLInterpreterObject
{
public:
  CTCLTimer ();
  CTCLTimer(CTCLInterpreter* pInterp, UInt_t nMsec = 0);
  virtual ~CTCLTimer ( );


  Tk_TimerToken getToken() const;
  UInt_t getMsec() const;
  Bool_t IsSet() const;

  virtual   void operator() ()   = 0;

  void Set ()  ;
  void Set(UInt_t nms);
  void Clear ()  ;
};


    
```

<a name="AEN44933"></a>## DESCRIPTION

Tcl/Tk provide a mechanism for scheduling functions to be executed
            after a time delay specified in milliseconds.   The `CTCLTimer`
            class is an abstract base class that provides an interface into the API
            for that facility.  To use `CTCLTimer` you must
            create a class derived from `CTCLTimer` that
            overrides and implement the `operator()` function.
            Create an object from the resulting function class.  Use the object's
            `Set` and `Clear` members to schedule
            or cancel a scheduled execution.  The code fragment
            example below shows how to do this
            to create a class that periodically emits the text "Tick" to stderr.
            Many #include directives are missing for brevity.

<a name="AEN44942"></a>```
Ticker
```

<a name="AEN44946"></a>## METHODS

<a name="AEN44948"></a>```
CTCLTimer
```

Construct timer objects.  The first form of the constructor creates a timer
            object that must be later bound into an interpreter via a call to
            `CTCLInterpreterObject`::`Bind`.
            The seconf form of the contructor creates a timer object that is already
            bound to `pInterp` and has an initial schedule delay
            of `nMsec`.

<a name="AEN44962"></a>```
  Tk_TimerToken getToken() const;
  UInt_t getMsec() const;
          
```

These two members access internal state of the object.
            `getToken` returns the Tk_TimerToken
            associated with the timer object.  This is the Tcl/Tk token that
            identifies the timer request to the interpreter.
            `getMsec` retrieves the current value of the delay parameter
            in milliseconds.

<a name="AEN44968"></a>```
  virtual   void operator() ()   = 0;
        
```

This function must be overidden and implemented in concrete timer classes.
            See the example in DESCRIPTION above.

<a name="AEN44971"></a>```

  void Set ()  ;
  void Set(UInt_t nms);
  Bool_t IsSet() const;
        
```

`Set` schedules the object for execution.  If
            `nms` is provided it is saved as the scheduling
            parameter and determines the delay
            in milliseconds before `operator()` is
            next called.  If not provided, the most recently used delay will be
            used again.

`IsSet` returns kfTRUE if the
            timer is currently pending, or kfFALSE if no pending
            timer request is active.



<a name="AEN44982"></a>```
  void Clear ()  ;
        
```


If a Timer request is pending, cancels it.  If no timer request is pending,
            this function does nothing, and does not report an error.

<a name="AEN44985"></a>## SEE ALSO

CTCLInterpreterObject(3)

<a name="AEN44988"></a>## REFERENCES



<a name="AEN44991"></a>```
STL Tutorial and Reference Guide
```

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CTCLString | Up | CTCLLiveEventLoop |
