|  |  |  |
| --- | --- | --- |
| SpecTcl Command Reference. |
| Prev |  | Next |


---

# <a name="AEN3059"></a>roottree

<a name="AEN3063"></a>## Name

roottree -- Write CERN ROOT Trees.

<a name="AEN3066"></a>## Synopsis

**roottree create *tree-name parameter-pattern-list ?gate?*
**

**roottree delete *tree-name*
**

**roottree list *?tree-name-pattern?*
**

<a name="AEN3076"></a>## DESCRIPTION

This command allows SpecTcl to write  root trees from the
            unpacked parameters.  Root Tree writers act as a
            Event sink, but are linked to an event processor so that they
            are aware when run start/stop records are encountered.

The create subcommand creates a new
            tree named `tree-name` the parameters
            that match any of the list of glob patterns in
            `parameter-pattern-list` will be written to the
            tree.  If `gate` is supplied, branches will
            only be written to the tree for events that satisfy that
            gate name.

The delete subcommand deletes the root
            tree named by `tree-name`.  Deleting the
            tree does not remove it from any open Root file.  All it does is
            prevent that tree from having any further branches written in any open
            root file and from existing in any future root file.

The list subcommand produces a Tcl list
            of trees that are currently defined.  If the glob-pattern
            `tree-name-pattern` is supplied, only those
            trees whose names match that pattern will be listed.  If
            `tree-name-pattern` is omitted, the default
            glob pattern, *, matches all trees.

The output of the list subcommand is
            a Tcl list of tree descriptions.  Each description consists of a
            three element sublist.  The elements of that sublist are, in order,
            The tree name, the list of parameter patterns defining the
            written parameters and the name of the gate that conditionalizes
            branch creation in the tree.  If no gate was selected, this will
            be the string -T- indicating a True gate is
            used.

The name of the root file written is
            run-*runnumber*.root
            in the current working directory of the login.  If it's necessary to
            write trees but no begin run item has been seen, the trees will be
            written to the file SpecTcl-*seq*.root
            where *seq* is the number of times we've been
            asked to start writing tree data without seeing a start.

Typically the case of not seeing a start occurs when attachingh to
            an online data source.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| rootexec | Up | pman |
