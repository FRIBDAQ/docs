|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 50. NSCL DAQ Thread Library | Next |


---

# <a name="AEN9734"></a>50.3. Using CGaurdedObject to implement synchronized methods

The `CGaurdedObject` class provides a base class that can be 
	used for classes that must require some or all of their methods only be run by
	one thread at a time.  The class incorporates a mutex as private class data.  It also 
	provides `Enter` and `Leave` methods
        that take and release the mutex respectively.

Below is a typical use pattern for this class:

<a name="AEN9741"></a>**Example 50-5. Using `CGaurdedObject`**

```
#include <GaurdedObject.h>              
...

class MyClass : public CGaurdedObject    
{
   void someProtecedMethod();            
...
}

...
void
MyClass::someProtectedMethod()
{
   Enter();                             
    ...
   Leave();                             
}
	
```

[[x9734#gaurded_include]]	    The header CGaurdedObject.h defines the
	    `CGaurdedObject` class and must be included
	    by classes that derive from that class.
	  [[x9734#gaurded_inherit]]	    The `CGaurdedObject` must be derived from
	    to be useful.  Here we define the `MyClass`
	    as a derivation of `CGaurdedObject`.
	    What this normally means is that `MyClass`
	    has one or more methods that must be synchronized between threads.
	    The concept of a method that can only run in one thread of execution
	    was developed/discovered by Per Brinch-Hansen, and C.A. Hoare in 1972.
	  [[x9734#gaurded_enter]]	    Invoking the `Enter` method of the base class
	    enters the monitor.  You can think of this call as your execution flow
	    entering a gate that only admits one execution thread at a time.  If a 
	    thread is already executing code following an `Enter`
	    call any other thread will block until the corresponding `Leave`
	    call is executed.  Note that the underying mutex is a recursive mutex so that if a thread
	    already in a monitor needs to call another protected method in the same class it
	    will not block.
	  [[x9734#gaurded_leave]]	    The `Leave` indicates the end of execution of a monitor.
	    If there are threads waiting at an `Enter` for the same
	    object one of them is scheduled for execution, and therefore enteres the monitor.

Note that the monitors implemented by `CGaurdedObject` are
	object global, that is only one thread can execute in an `Enter`,
	`Leave` over the entire object.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Incorporating the library into an application. | Up | Thread safe queues (CBufferQueue). |
