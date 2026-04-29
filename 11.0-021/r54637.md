|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="rdogui3_outputwindowsettings"></a>OutputWindowSettings

<a name="AEN54649"></a>## Name

OutputWindowSettings -- Prompter for `OutputWindow` settings.

<a name="AEN54653"></a>## Synopsis

**OutputWindowSettings *widget-path ?options...?*
**

<a name="AEN54657"></a>## DESCRIPTION

This megawidget provides a prompter for options that can be applied to
            a
            [[r54125#rdogui3_ui_OutputWindow]]
            widget.  A convenience proc is also provided that wraps this widget
            in a dialog and, when the user accepts the state of the dialog,
            changes the configuration options of the
            `OutputWindow` singleton appropriately.

<a name="AEN54662"></a>## OPTIONS

The widget accepts the standard `configure`
            and `cget` methods.  These operate on the
            following set of options:



`-rows` *row-count*Sets/gets the number of rows requested from the
                         prompter (this is controlled by a spinbox widget).

`-columns` *column-count*Sets/gets the number of columns requested from the
                         prompter.   This is controlled by a spinbox widget.

`-history` *history-lines*Sets/gets the number of lines of history information
                         requested from the prompter.  This is controlled
                         by a spinbox widget.

`-debug` *1 | 0*Gets/sets the state of the checkbutton widget that is
                         labeled Show debugging Output.

<a name="AEN54693"></a>## CONVENIENCE PROC

`::Output::promptSettings` displays a
                `OutputWindowSettings` widget wrapped in a
                [[r52946#rdogui3_dialogwrapper]].
                If the user clicks Ok, the proc fetches
                the singleton `OutputWindow` and sets its
                options accordingly.

The Show debugging Output checkbox is handled
                by making or removing a debug entry in the `OutputWindow`'s
                `-showlog` dict for the debug class.
                The contents of this entry, when present, are empty resulting
                in default text rendition.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| ui | Up | StatusArea |
