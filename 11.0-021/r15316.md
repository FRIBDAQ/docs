|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="tcl1_gdgpanel"></a>!ModuleName!

<a name="AEN15328"></a>## Name

gdgpanel -- Tabbed notebook for multiple GDG-8 controllers.

<a name="AEN15331"></a>## Synopsis

**gdgpanel
        **

<a name="AEN15334"></a>## DESCRIPTION

This Tk script processes a control configuration file enumerating the
          WIENER/JTECT gdg8 modules that it defines.  For each module created in that
          file, a tab in a tabbed notebook is created that contains a control panel
          for that module.

See ENVIRONMENT VARIABLES below for information
          about how to control the operation of this script.

<a name="AEN15339"></a>## ENVIRONMENT VARIABLES

Several environment variables (which have reasonable default values
          if not defined) control the operation of this script:



CONTROLHOSTDefines the host on which the VMUSBReadout program is running.
                      If not defined, this defaults to
                      localhost, that is the same system
                      on which the control panel is running.

CONTROLPORTSpecifies the server port on which the VMUSBReadout
                      control server is listening for connections. This defaults
                      to 27000 which is also the default
                      used by VMUSBReadout unless `--port`
                      is used when invoking that program to override the
                      default.

CONFIGDIRThe directory in which the control configuration
                      file lives.  This defaults to
                      ~/config

CONFIGFILEWhen joined with CONFIGDIR, determines
                      the full path to the control configuration file.
                      This defaults to controlconfig.tcl.
                      This is the default unless overriden by the
                       `--ctlconfig` option on the
                       VMUSBReadout command line.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| serverauth | Up | ledph7106.tcl |
