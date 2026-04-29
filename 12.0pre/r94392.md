|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="tcl3.tclsourcefilter"></a>TclSourceFilter

<a name="AEN94406"></a>## Name

TclSourceFilter -- Extract blocs mathing a regexp from a script

<a name="AEN94409"></a>## Synopsis

**TclSourceFilter *name* | %AUTO%
          **

** *name* SetValidPatterns *pattern-list*
**

** *name* Filter *tcl-script-fragment*
**

<a name="AEN94421"></a>## DESCRIPTION

Provides a mechanism to extract script blocks that match a list of
            regular expressions.

<a name="AEN94424"></a>## METHODS



`SetValidPatterns` pattern-listSets the regular expressions that will be matched
                                to `pattern-list`.
                                `pattern-list` is a
                                valid Tcl list whose members are regular
                                expressions.

`Filter` tcl-script-fragmentReturns a list of strings.  For each valid Tcl
                                command block in the string
                                `tcl-script-fragment`,
                                if that block matches against at least one of
                                the regular expressions established by
                                `SetValidPatterns`,
                                the content of that block (sans any outer
                                braces) is added to the return value list.

The result of this command is a list whose elements
                                are the contents of the matching blocks.  An
                                empty list is, of course, a possible return value.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Process | Up | Utils |
