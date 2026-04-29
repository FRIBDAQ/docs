|  |  |  |
| --- | --- | --- |
| SpecTcl Programming Reference. |
| Prev |  | Next |


---

# <a name="AEN3671"></a>CTreeVariable

<a name="AEN3675"></a>## Name

CTreeVariable -- Access to Tcl variables with metadata

<a name="AEN3678"></a>## Synopsis

```
CTreeVariable
```

<a name="AEN3681"></a>## DESCRIPTION

The `CTreeVariable`  class provides
                    simplified access to Tcl intepreter variables.  These
                    variables are globally scoped variables in Tcl and
                    are defined in the interpreter that executes
                    SpecTcl commands.

The operations provided by the class are sufficient
                    to allow you to treat the tree variable as if it were
                    a simple double value, transparently fetching or
                    storing the underlying Tcl variable as needed.

Tree variables also have metadata.  Specifically each tree
                    variable can have a unit of measure property.

<a name="AEN3688"></a>## METHODS

Constructors and initializers.  As with tree parameters,
                    tree variables support both one and two step
                    construction.



`  CTreeVariable();`This default constructor will require that
                                you later invoke
                                `Initialize`
                                to complete the two step construction of the
                                object.

`  CTreeVariable( std::string  name,  double  value,  std::string  units);``name` is the name of
                                the Tcl variable this object is
                                associated with.  `value`
                                is an initial value the variable will be given.
                                `units` are the units
                                of measure metadata to be associated
                                with this variable.

If there is already a Tcl variable, this does
                                not affect it.  The variable will need to be bound.
                                first.  If there is already a tree variable,
                                The previously established
                                initial value and units override the value and
                                units in this constructor.

A bit of information about how all this works
                                that will help you to understand some of the
                                pathalogical cases.  Tcl supports linking
                                a C/C++ variable to a Tcl variable.  We
                                use this, however we have to do some fancy
                                footwork to support many to one mappings from
                                tree variables to Tcl variables.

Associated with a tree variable name and,
                                therefore, with all tree variable objects
                                with the same name, is a properties object.
                                The properties object contains the name,
                                value and units metadata, shared between
                                all tree variables objects with the same name.
                                Binding at least one of the objects links the
                                C++ variable containing the value with the
                                Tcl variable with the same name as the
                                tree variable's name.

Thus, unlike tree parameters, once a
                                tree variable is constructed, it can be set,
                                gotten, modified and queried without error.
                                What does not happen is for anything done to the
                                value of the tree variable to affect the
                                Tcl variable.  Binding the tree variable
                                links the data containing the value with the
                                Tcl variable and ensures that the Tcl variable
                                has the current value of the tree variable.

A short code segment may be useful.

```
CTreeVariable t1("myvar", 1234, "arb");           // Tcl variable unchanged
CTreeVariable t2("myvar", 456, "inch");           // Tcl and tree variable unchanged.

t1 = 777;        // T1 and T2 are now 777, Tcl variable unchanged.
t2.Bind();       // Tcl variable now 777.

t1 = 0;          // Tcl, t1, and t2 vars are now 0.
                            
```

`  CTreeVariable( const CTreeVariable&  rhs);`Copy construction.  This allows tree variables
                                to be passed by value.  Since, however all like named
                                tree variables use the same underlying data,
                                Changes to the copy constructed object will be
                                reflected in all other like named tree variables and,
                                if the variable is bound, in the Tcl variable.

Thus, while pass by value is legal, it has the
                                semantics of pass by reference.

`   void  Initialize( std::string  name,  double  value,  std::string  units);`Second step of two step initialization. The
                                parameters have the same meaning as in the one-step
                                construction constructor.

The next set of methods are provided so that, for the most part,
                    you can treat a `CTreeVariable` as if it
                    were a Double precision variable.  The main contributor to this
                    is the `operator double` conversion
                    operator.  This operator allows a `CTreeVariable`
                    variable in an expression to be converted to a double, supporting
                    its use on the right hand side (as an r-value) of assignments.



`  const  operator double();`In C++ this sort of method is called a
                                conversion operator, or casting operator.
                                It provides a method that allows
                                `CTreeVariable`
                                objects to be treated as double variables
                                wherever appropriate.
                                The method returns the value of the
                                underlying variable.  Note that if the
                                object has not yet been bound, the value
                                returned is the most recently set value of
                                the object, which can differ from the
                                Tcl variable's value.

`   CTreeVariable&  operator=( double  rhs);`Assignment operator.  This is one of the
                                operators that allows
                                `CTreeVariable` objects
                                top be used on the left hand side of
                                assignment operations (as an l-value).
                                The method assigns the
                                double `rhs`
                                to the value of the variable. If the
                                object has been bound, this will be the new
                                value of the Tcl variable.  If not, this value
                                will be held in the variable and will become
                                the value of the Tcl variable when it is bound.

By returning a reference to the object, assignment
                                chaining is supported,  e.g. like

```
CTreeVariable t1("avar", 1.234, "arbitrary");
double        d1;

d1  = t1 = 5.6;             // d1 is 5.6 as is t1.
                            
```

The best way to read the last statement is
                                right to left.  First the tree variable is
                                given the value 5.6 and that assignment can be
                                thought of as being replaced by the
                                `t1`  tree variable reference.

To accomplish the assignment to `d1`,
                                the `operator double`
                                is used to returne the value of
                                `t1` to assign to
                                `d1`

`   CTreeVariable&  operator=( const CTreeVariableamp;  rhs);`Assigns the value of the `rhs`
                                tree variable to the value of this variable.
                                Once more returning a reference to the object
                                allows operator chaining.

`   CTreeVariable&  operator+=( double  rhs);`Like assignment, but `rhs`
                                is added to the variable's value.

`   CTreeVariable&  operator-=( double  rhs);`Like assignment but
                                `rhs` is subtracted
                                from the value of the object.

`   CTreeVariable&  operator*=( double  rhs);`Like assignment but
                                `rhs` multiplies the
                                object's value.

`   CTreeVariable&  operator/=( double  rhs);`Like assignment but the value of the object is
                                divided by the `rhs`.

`   double  operator++( int  dummy);`This operator is the post-increment operator.
                                The value of the object prior to the increment
                                is returned.  Because of the binding to an underlying
                                Tcl variable, the normal semantics of  predecrementing
                                are not possible.

Specifically  normally post-increments ill return
                                a copy of the object prior to the increment, while
                                here a double is returned instead.  In most cases
                                you won't notice the difference.

`   CTreeVariable&  operator++();`Pre-increment operator.  The variable's value is incremented
                                and then a reference to the object is returned.

`   double  operator--( int  dummy);`Post decrement operator.  The value of the object
                                is decremented but the value returned is the
                                double value prior to the increment.

`   CTreeVariable&  operator--();`Pre decrement operator.  The object's value is
                                decremented after which a reference to the
                                decremented object is returned.

The next set of operations can be best described as
                    queries about the object.



`   std::string  getName();`Returns the name of the object, and hence
                                the Tcl variable the object represents.

`   double  getValue();`The same as `operator double`.
                                The value of the object is returned.

`   std::string  getUnit();`Returns the units of measure metadata for the
                                object.

`   bool  hasChanged();`Each tree variable has an associated flag
                                that is set true
                                when the definition of that variable
                                has changed.  This method returns the
                                value of that flag.

The main purpose is to control which parameter
                                definitions might need to be written
                                to file during a state save operation.

`   bool  valueChanged();`Each variable has a value changed
                                flag as well that is modified when the
                                value of the variable is modified.
                                This is normally used to fire traces
                                on a variable in Tcl.

`   void  resetChanged();`Resets both changed flags described above and
                                fires any value changed Tcl traces.  Traces are
                                used by Tk widgets to know when to update
                                values they contain via `-variable`
                                and `-textvariable` options.
                                It is therefore important to ensure that
                                these traces get fired after C++ changes
                                to these values if there are user interface
                                elements that display these variables.

The remainder of the methods primarily relate to bindings,
                    the registry of variables,
                    and the interface of the variable to its Tcl counterpart.



`   void  Bind();`Binds this variable to the Tcl variable of the
                                same name, creating it if necessary.  The
                                object's value will be put into the Tcl variable.
                                If the object is already bound this is a silent
                                No-op.

` static   void  BindVariables( CTCLInterpreter&  rInterp);`A registry is maintained of all tree variable
                                objects.  This method iterates this registry
                                and binds all tree variables to their underlying
                                Tcl variables.  You can think of this as
                                invoking `Bind` on every
                                tree parameter.

` static   TreeVariableIterator  begin();`, ` static   TreeVariableIterator  end();`, ` static   TreeVariableIterator  find( std::string  name);`Return pointer like objects that can be
                                used to iterate the tree varaible registry.
                                When dereferenced, the object returns a
                                `std::pair<std::string, CTreeVariableProperties*>`
                                The first item of each pair is the name of the
                                tree variable.  The second are the set of
                                properties that are shared between all
                                variables of the same name.

`CTreeVariableProperties`
                                will be described later in this reference section.

`begin` returns the
                                iterator 'pointing' to the first object in the
                                container.
                                Incrementing an iterator  'points' it to the
                                next tree variable in the container.  Incrementing
                                the iterator pointing at the last object in the
                                container returns a value equal to that returned
                                by `end`.

`find` returns an iterator
                                that points to the item in  the container named
                                `name`.  Note that since
                                the registry contains `CTreeVariableProperties`
                                objects, there won't be duplication.
                                I there is no entry in the registry with the
                                `name`, the value
                                returned from `end`
                                is returned.

` static   int  size();`Returns the number of entries in the
                                registry.  Note that since the registry
                                contains
                                `CTreeVariablePropertiew`
                                objects, the number of entries in the registry
                                may be less than the number of
                                `CTreeVariable` objects that
                                have been created.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| CTreeParameterArray | Up | CTreeVariableProperites |
