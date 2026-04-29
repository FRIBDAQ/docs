|  |  |  |
| --- | --- | --- |
| genx - system for framework independent analysis. |
| Prev |  | Next |


---

# <a name="AEN771"></a>Chapter 6. Adding a `--target` to the genx compiler.

The **genx** command is actually a driver that puts together
				a pipeline in which the parser pass feeds the intermediate representation
				to the code generating pass.  This command's code is in the
				genx subdirectory of the directory tree.

To add a target you must:



1. Make the genx program recognize your new target in the
   					`--target` option.
2. Make the genx program build the correct pipeline for your new target.

genx uses **gengetopt** to process command parameters.
				**gengetopt** takes genxparams.ggo
				as input and creates a header and C file to parse the parameters and options.
				Locate the following line in that file:

<a name="AEN788"></a>```
option "target" t "Code generation target" values="spectcl","root" enum
				
```

Add your target name to the list of target names in the
				values clause of this line.

Next you'll need to modify the genx.cpp compiler driver to select the
				correct backend for your option.  Suppose your new target is called
				mytarget and is implemented in a program named
				mygenerator that will be installed in the genx installation's
				bin directory.

Locate the following code snippet in genx.cpp:

<a name="AEN797"></a>```
    if (parsedArgs.target_arg == target_arg_spectcl) {
        backend += "specgenerate";
    } else {
        backend += "rootgenerate";
    }
				
```

Modify it to look like:

<a name="AEN800"></a>```
    if (parsedArgs.target_arg == target_arg_spectcl) {
        backend += "specgenerate";
    } else if (parsedArgs.target_arg == target_arg_root) {
        backend += "rootgenerate";
    } else if (parsedArgs.target_arg == target_arg_mytarget) {
				    backent += "mygenerator";
				}

				
```

Note that since gengetop's parameter parsing code ensures the value of
				`--target` is one of the values specified, there's no need
				(though it can't hurt) for a final else to report an
				illegal value.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Programming manual | Up | Writing a generator |
