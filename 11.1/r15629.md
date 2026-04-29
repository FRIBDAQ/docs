|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="manpage.vmetcl"></a>SBS Vme Tcl package

<a name="AEN15633"></a>## Name

vme -- Provide access to VME crates to Tcl scripts.

<a name="AEN15636"></a>## Synopsis

**vme create *mapname* ?options? *base* *size*
**

**vme delete *mapname*
**

**vme list
    **

** *name* get -l|-w|-b *offset*
**

** *name* set -l|-w|-b *offset value*
**

<a name="AEN15655"></a>## DESCRIPTION

The **vme** command allows you to create, destroy and
        list a set of address windows into the VME card crate.  Maps are named
        entities.  When a map is created, the package also creates a command named
        after the map.  This command is then used to access them map via its ensemble
        **get** and **set**commands.

<a name="AEN15661"></a>### vme create

Creates a new map.  The *mapname* parameter
            is the name of the map and, on success, is created as a new command
            that can be used to access them.
            *base* and *size*
            define the address window base address and size.

The following options are recognized:



`-device` *type*Defines the address modifier associated with this
                            map.  This should be one of
                            extended (32 bit address space),
                            standard (24 bit address space),
                            shortio (16 bit address space)
                            or geo (slot addressing for crates
                            and modules that support this.

`-crate` *n*Selects a VME crate other than the default crate 0.
                            If not provided this defaults to zero.

<a name="AEN15685"></a>### vme delete

Deletes an existing map.  All device and driver resources are destroyed.
            The command created to access the map is removed from the interpreter.

<a name="AEN15688"></a>### vme list

Lists the set of VME maps defined by this script via this package.
            The maps are returned as the command result.  The result is a list
            of two element sublists. Each sublist contains, in order, the name of the map
            and the base address of the map in VME space.

<a name="AEN15691"></a>### Map access command

When a VME map is created, the name of the map also becomes a new
            Tcl command.  That command is a command *ensemble*
            that allows your script to access the address window defined by the
            map.

A Tcl command ensemble is a command that has subcommands.  The
            subcommands the map has are **get** which fetches
            data fromt he address window and **put** which
            puts data into the address window.

The format of the *mapname* **get**
            command is:

<a name="AEN15701"></a>***mapname* get *width offset*
**

THe format of the *mapname* **put**
            command is:

<a name="AEN15709"></a>***mapname* put *width offset value***

These commands have some common elements.  Specifically, *offset*
            is a byte offset into the map at which the get or put is performed.
            *width* is anoption which describes the width of the
            data transfer.  This can be any of:



`-l`Transfer will be of longword (32 bit) width.

`-w`Transfer will be of word (16 bit) width.

`-b`Transfer will be of byte (8 bit) width.


The `data` on the **put**
            subcommand is the data that is actually written to the VME
            bus.  Only the appropriate number of low order bits is used.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| cratelocator | Up | epicsdisplay |
