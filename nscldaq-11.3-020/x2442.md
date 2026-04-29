|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 5. CCUSBReadout | Next |


---

# <a name="AEN2442"></a>5.3. Writing device support software

This section describes how to write a device support module.
            Device support modules are built into shared object libraries
            that can be dynamically loaded into the readout software via
            the **load** command.

The device support package is provided as a template driver
            source file and a Makefile that builds the shared object.
            If the DAQ software is installed in $DAQROOT, the following
            commands copy the template driver and its makefile:

<a name="AEN2447"></a>**Example 5-4. Obtaining the ccusb driver development kit**

```
cp $DAQROOT/ccusbdriver/drivertemplate.cpp .
cp $DAQROOT/ccusbdriver/Makefile .
            
```

The example below shows how to load a user written driver
            and use the driver that is created by an unmodified driver template:

<a name="AEN2453"></a>**Example 5-5. Using a user written CCUSB driver**

```
set here [file nativename [file dirname [info script]]]
load [file join $here libtemplatedriver.so]
changeme create testing -value 0x1234
            
```

The example assumes that you have built the driver in the same
            directory as your configuration file.  The first example line
            computes the full file path to the configuration file's directory.
            The second loads the driver, joining that path to the name of the
            shared object created by the Makefile.  Note that you typically will
            need to provide a full path to the driver shared object or the
            **load** command will claim the file cannot be located.
            The final command creates and configures a device instance
            named testing using the **changeme**
            command the unmodified driver creates.

Let's look at the template driver you copied.
            The template consists of two main chunks.  The first chunk is a
            class derived from `CReadoutHardware` that is
            responsible for managing the driver itself. You will normally
            need to modify the `onAttach`,
            `Initialize` and `addReadoutList`
            methods of this class, as well as changing the class name to something
            more reasonable than `CTemplateDriver`.

The second chunk is a Tcl package initialization function that
            must define the Tcl command that is associated twith the driver.

While the driver template is heavily commented, and modification
            points are indicated, the next few sections are a guided tour
            of the main sections you will need to modify.

## <a name="AEN2468"></a>5.3.1. The driver onAttach method

Each driver instance has a configuration database attached to it
                when it is created.  The configuration database holds configuration
                parameter definitions and their current values.  The framework
                takes care of managing the values for you, however you must
                define the set of configuration parameters supported by your
                driver.

The template driver's code is (comments removed for brevity:

<a name="AEN2472"></a>```
void
CTemplateDriver::onAttach(CReadoutModule& configuration)
{
  m_pConfiguration = &configuration;                    
  m_pConfiguration->addIntegerParameter("-slot", 1, 23, 1); 

  m_pConfiguration->addIntegerParameter("-value"); // default is 0. 
}
                
```

[[x2442#ccusb-dtemplate-saveconfig]] `onAttach` needs to be able
                        to access its configuration in other methods.
                        The `configuration` parameter is
                        a reference to that configuration.  This line
                        saves a pointer to that configuration in the
                        `m_pConfiguration` member variable.
                        Note that a `CReadoutModule`
                        is derived from a `CConfigurableObject`
                        and that base class holds the configuration.
                    This code is provided by the driver template.

[[x2442#ccusb-dtemplate-slotparam]]                        Virtually all of the device support you write will
                        need to know which slot in the CAMAC crate contains
                        your module.  This line creates an integer
                        parameter constrained to lie in the range
                        [1..23] named -slot.
                        The default value (if the user does not configure
                        this item) is 1 (the last parameter
                        of the `addIntegerParameter` call).
                    This code is provided by the driver template.

[[x2442#ccusb-dtemplate-valueparam]]                        This sample line shows how to create an unconstrained
                        integer parameter named -value.
                        The configuration subsystem will ensure the value
                        is a valid integer but will not contrain the range
                        of that integer.
                    This line is provided by the template driver but normally
                        is removed as you edit the code to define the
                        configuration options you actually need.

Normally the `onAttach` method is simply
                defining the set of configuration parameters it needs to know
                how to initialize and read the device it manages.  Configuration
                parameters are named items (by convention the names start with the
                dash character) and are strongly typed. Integer, real, string,
                enumerated, and boolean simple parameters are supported.  In
                addtion collection (Tcl lists) are supported.

Parameter values can have constraints placed on them (the
                range of `-slot` parameter values e.g.) which
                are checked by the configuration subsystem without any intervention
                by you.  Several pre-defined constraint checkers are available,
                as are convenience functions for defining configuration parameters.
                You can also define custom constraint checkers and register them
                with the configuration subsystem.

See [[r52676]] for
                detailed information about how to define configuration
                parameters.

## <a name="AEN2503"></a>5.3.2. The driver Initialize method

The `Initialize` method of each
                device instance that has been put in a stack is called
                after the configuration file is processed prior to loading
                the stack and prior to turning on data taking mode in the
                CC-USB.

Typically in `Initialize` you must:



1. Fetch the configuration parameters you need
                               to know how to initialize the device and prepare
                               it for data taking.
2. Issue method calls to the `controller`
   `CCCUSB` object passed in to the
                               method.  Note that if your device requires a lot of
                               initialization, you can speed up that process
                               by creating `CCCUSBReadoutList`
                               objects, which are lists of instructions, using
                               its methods to create a list of operatinos and then
                               asking the controller to execute that list.


For detailed information about the methods supported by
                the `CCCUSB` and `CCCUSBReadoutList`,
                see [[r48902]] and [[r52151]]

The template driver provides the following code (most
                comments removed for brevity).

<a name="AEN2523"></a>```
void
CTemplateDriver::Initialize(CCCUSB& controller)
{

  int slot = m_pConfiguration->getIntegerParameter("-slot"); 

  /* MODIFY ME HERE */
                                                             
  /* END MODIFICATIONS */

}


                
```

[[x2442#ccusb-dtemplate-init1]]                        In most cases you need the slot number of the module
                        to initialize it.  This call obtains the value of the
                        `-slot` configuration parameter
                        from the configuration database for this module.
                    [[x2442#ccusb-dtemplate-init2]]                        You would add code here to fetch parameter values
                        as well as method calls for the `controller`
                        object to manipulate the CAMAC crate.  If initialization
                        requires a large number of CAMAC operations you could
                        also create a `CCCUSBReadoutList`,
                        manipulate it to store a set of operatiuons and then
                        use `controller.executeList(3ccusb)` to
                        execute that list.

## <a name="AEN2536"></a>5.3.3. The driver addReadoutList method

`addReadoutList` is called as a run is
                being intialized.  This method is expected to contribute items
                to the `CCCUSBRedoutList` that will be
                loaded into either a scaler or event stack.  Usuall this is done
                by fetching the set of configuration parameters that are required
                to know how to read the device and then invoking appropriate
                methods on the `list` parameter to
                add CAMAC operations to the stack.

The template driver implements a marker 'device'. The marker
                device ignores its `-slot` configuration parameter
                (a production quality marker driver would probably not define
                a `-slot` parameter).  It adds an instrution
                to the `list` that inserts a  literal
                value into the event.  The value inserted is determined by
                the `-value` parameter.

Here's the sample driver code for the `addReadoutList`
                method:

<a name="AEN2549"></a>```
void
CTemplateDriver::addReadoutList(CCCUSBReadoutList& list)
{
  int slot = m_pConfiguration->getIntegerParameter("-slot");
  
  /* MODIFY ME HERE */
  
  int value = m_pConfiguration->getIntegerParameter("-value");  
  list.addMarker(value);        // This is a longword marker.   

  /* END MODIFICATIONS */
}

                
```

[[x2442#ccusb-dtemplate-read1]]                        This line fetches the `-value`
                        cofiguration parameter.  This is the value
                        that we are going to insert into the event buffer
                    [[x2442#ccusb-dtemplate-read2]]                        The `addMarker` method adds
                        the CCUSB instructions to insert a literal value in the
                        output buffer to the list being built up. This
                        therefore instructs the CCUSB that the readout of this
                        'device' consists of inserting the value of the
                        `-value` configuration parameter.
                    Naturally a real device would add NAF instructions or
                        Q-Stop/C-Scan operations to the list via other
                        `CCCUSBReadoutList` methods.

## <a name="AEN2563"></a>5.3.4. Initializing the driver with the framework.

The Tcl **load** command searches the
                shared object for a specific function entry point that
                it will call to initialize the library.  The initialization function
                must follow the correct naming conventions or Tcl will complain
                about not being able to find the library's initialization function.

The initialization entry point must be the name of the
                resulting library with the lib prefix stripped
                off and the first letter capitalized suffixed by _Init.
                Thus if you are building
                libmydriver.so, the initialation function
                must be called `Mydriver_Init`.

The template driver provides the following code:

<a name="AEN2573"></a>```
extern "C" {                                    
  int Templatedriver_Init(Tcl_Interp* pInterp)  
  {
    Tcl_PkgProvide(pInterp, "Templatedriver", "1.0"); 
 
    CUserCommand::addDriver("changeme", new CTemplateDriver); 

    return TCL_OK;                               

  }
}
                
```

[[x2442#ccusb-dtemplate-dinit1]]                        Since C++ *decorates* function  names
                        with an encoding of the call signature, to support function
                        overloading, you must declare the initialization
                        functino using C linkage conventions.  The
                        extern "C" {} creates a block of
                        code whose externally visible symbols will use C
                        linkage conventions.
                    [[x2442#ccusb-dtemplate-dinit2]]                        In general you will need to modify the name of this
                        to work with the name of the library file you
                        create.  The discussion prior to this example
                        describes the naming conventions that are required.
                    [[x2442#ccusb-dtemplate-dinit3]]                        In our examples we used the Tcl **load**
                        command to load the driver.  This statement registers
                        the library as providing a Tcl loadable package.
                        You can use the Tcl command **pkg_mkIndex**
                        to build an auto load index file for loadable packages
                        including those in shared libraries.  This allows you
                        to collect several drivers into a directory added to the
                        auto load path, and use the **package require**
                        command to load them by package name.  You must
                        change the name of the package in this call
                        to be something unique and descriptive of your driver.
                    [[x2442#ccusb-dtemplate-dinit4]]                        The `CUserCommand`::`addDriver`
                        function associates a template device driver object
                        with its Tcl command ensemble name.  The template device driver
                        object is cloned for each **create** subcommand
                        issued for this driver in the configuration script.
                        You should change both the name of the driver command
                        from changeme and you should have
                        previously changted the class name of the
                        driver class from `CTemplateDriverM`
[[x2442#ccusb-dtemplate-dinit5]]                        If the library initialization was successful it
                        should return TCL_OK on failure
                        it shouild return TCL_ERROR.
                        In this case it is also customary to use
                        e.g. Tcl_SetResult or a similar function to set the
                        result of the load command to a descriptive error
                        message.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Writing DAQ configuration files | Up | Tcl device driver support |
