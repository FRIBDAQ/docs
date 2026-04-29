|  |  |  |
| --- | --- | --- |
| SpecTcl Python package |
| Prev |  | Next |


---

# <a name="AEN716"></a>variable

<a name="AEN720"></a>## Name

variable -- Wrapper for SpecTcl tree variable objects.

<a name="AEN723"></a>## Synopsis

```
class spectcl.variable:
```

<a name="AEN762"></a>## DESCRIPTION

Tree parameter objects have one constructor form that
                        takes a single positional parameter. This parameter
                        is a string that contains the name of an existing
                        treeparameter.

<a name="AEN765"></a>## ATTRIBUTES

In addition to being able to retrieve the name of the
                        parameter, you can use the object attributes
                        to set the value and units of a treevariable.

Attributes are:



` readonly string  name;`This attribute contains the name of the
                                    tree variable.  It cannot be written.

` read/write double  value;`Gets or sets the tree variable value.

` read/write string  units;`Gets or sets the units of measure associated
                                    with this tree variable.

<a name="AEN794"></a>## METHODS



`    def valchanged() :`Returns the value changed flag.
                                    This is set once the value has been changed
                                    from the initial value set at compilation time.
                                    The normal use for this method is to determine
                                    if the tree variable must be saved in order
                                    to be able to restore the current state of
                                    SpecTclfrom file.

`    def defchanged() :`Returns the definition changed flag.
                                    This is True if the
                                    units have changed.  The major use for this
                                    is to determine if the variable must be saved
                                     in order for the SpecTcl state to be
                                     restored from file.

`    def reset() :`Resets the flag returned from
                                    `defchanged`

`    def fireTraces() :`The value of tree variables are mapped to
                                    Tcl variables of the same name.  These
                                    in turn may be used as GUI elements or
                                    explicit traces may be set on them in the
                                    user's Tcl code.

Calling this method fires any pending
                                    traces for the variable.  Firing the
                                    traces on a variable also resets its
                                    value changed flag.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| The spectcl.variable type | Up | The spectcl.gates type |
