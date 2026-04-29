|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="tcl3_ScaleControl"></a>ScaleControl

<a name="AEN71498"></a>## Name

ScaleControl -- Megawidget intended for axis scale control

<a name="AEN71501"></a>## Synopsis

**ScaleControl *widget-path*
**

** *widget-path* configure *option...*
**

** *widget-path* cget *option*
**

<a name="AEN71513"></a>## DESCRIPTION

Megawidget that provides support for a set of options, some of which
            can be incremented and decremented through, all of which can be
            accessed via a drop down menu, as well as an optional numeric value.
            The intent is to use the widget to provide a zoom control for axis
            scaling in plots.  The drop down menu might be stocked with a set of
            pre-defined zoom settings and additional settings (e.g. Custom...
            or Auto).

The + and - buttons
            can step through a subset of the items in the drop down menu.
            An optional Min control allows users to
            specify a minimum value for the axis.  This can be used if a signal
            is weakly varying along a high offset; Zoom and set the min value
            to something near that offset to allow you to view the varying
            part of the signal in more detail.

This widget is patterned after the zoom controls that appear in many
            program such as Adobe Acrobat™.

<a name="AEN71524"></a>## OPTIONS



`-menulist` *list of items*The set of items in the drop down menu is set to the list
                        items in the `-menulist` parameter.
                        The items have an index numbered from zero that reflects
                        their position in this list.

`-zoomrange` *low high*Specifies the subset of menu items the +
                        and - buttons will step amongst.
                        The argument is a two element Tcl list that specifies,
                        in order, the first and last element indices of the set of
                        `-menulist` items eligible for this sort
                        of selection.

`-current`Contains/sets the text of the currently selected item.
                        The value is not restricted to the set of values in the
                        menu.  If this is a zoom control, that fact can be used
                        to implement custom zoom values that are not in the menu.

Changes to this option value, whether via configuration
                        by the application or user interface interactions will
                        dispatch the `-command` script.

`-min`Contains/sets the minimum value.  Changes to the value,
                        either from the application via a configure or from
                        the user interface, dispatch the `-mincommand`
                        script.

`-enablemin` *on|off*Boolean value.  When true displays
                        the min value setting.  When false
                        does not.  This is useful for e,g, strip charts for which
                        an x axis minimum value has very little meaning.

`-command` *script*Specifies a script that is
                        called when one of the following happens:



- The + button is clicked to
                              advance the current menu selection
- The - button is clicked to
                              go backwards in the zoom list from the current menu
                              selection.
- A selection is made from the drop down menu.
- The `-current` is configured by
                              the application.

See the section SUBSTUTIONS below for
                        the script substitutions that are supported.

`-mincommand` *script*Specifies a script that is invoked when any of the
                        following occurs:



- The min control loses input focus.
- The user uses the Return or
                              Keypad Enter keys when focus
                              is in the min control.
- The `-min` option is configured.

See the section SUBSTITUTIONS
                        below.

<a name="AEN71602"></a>## SUBSTUTIONS

All event handling scripts for this widget support the following
                substitutions:



%WWidget path.

%SValue of the `-current` option.
                            This is a string not a menu index.

%MValue of the min control.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| RingStatus | Up | 3sbsReadout |
