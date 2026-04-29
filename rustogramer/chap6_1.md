Provide site root to javascript 

 Work around some values being stored in localStorage wrapped in quotes 

 Set the theme before any content is loaded, prevents flash 


 Hide / unhide sidebar before it is displayed 


1. [[**1.** Chapter 1 - Introduction|chapter_1]]
2. 1. [[**1.1.** How to use this book|chap1_1]]
3. [[**2.** Chapter 2 - Preparing data for Rustogramer|chapter_2]]
4. 1. [[**2.1.** The FRIB analysis pipeline|chap2_1]]
   2. [[**2.2.** Format of data Rustogramer accepts|chap2_2]]
5. [[**3.** Chapter 3 - Running Rustogramer|chapter_3]]
6. [[**4.** Chapter 4 - Using the Rustogramer GUI|chapter_4]]
7. 1. [[**4.1.** The Spectra Tab|chap4_1]]
   2. [[**4.2.** The Parameters Tab|chap4_2]]
   3. [[**4.3.** The Variables Tab|chap4_3]]
   4. [[**4.4.** The Gate Tab|chap4_4]]
   5. [[**4.5.** The BindSets Tab|chap4_bindsets]]
   6. [[**4.6.** The File Menu|chap4_5]]
   7. [[**4.7.** The Data Source Menu|chap4_6]]
   8. [[**4.8.** The Filters Menu|chap4_filters]]
   9. [[**4.9.** The Spectra Menu|chap4_7]]
   10. [[**4.10.** The Gate Menu|chap4_8]]
8. [[**5.** Chapter 5 - Using CutiePie to display histograms|chapter_5]]
9. [[**6.** Chapter 6 - the REST interface|chapter_6]]
10. 1. [[**6.1.** Tcl REST interface|chap6_1]]
   2. [[**6.2.** Python REST interface|chap6_2]]
11. [[**7.** Chapter 7 - Reference material|chapter7]]
12. 1. [[**7.1.** Command Line Options|chap7_1]]
   2. [[**7.2.** REST requests and responses|chap7_2]]
   3. 1. [[**7.2.1.** Response format|chap7_2_responses]]
      2. [[**7.2.2.** /spectcl/parameter requests|chap7_2_parameter]]
      3. [[**7.2.3.** /spectcl/rawparameter requests|chap7_2_rawparameter]]
      4. [[**7.2.4.** /spectcl/gate requests|chap7_2_gates]]
      5. [[**7.2.5.** /spectcl/spectrum requests|chap7_2_spectrum]]
      6. [[**7.2.6.** /spectcl/attach requests|chap7_2_attach]]
      7. [[**7.2.7.** /spectcl/analyze requests|chap7_2_analyze]]
      8. [[**7.2.8.** /spectcl/apply requests|chap7_2_apply]]
      9. [[**7.2.9.** /spectcl/ungate requests|chap7_2_ungate]]
      10. [[**7.2.10.** /spectcl/channel requests|chap7_2_channel]]
      11. [[**7.2.11.** /spectcl/evbunpack requests|chap7_2_evbunpack]]
      12. [[**7.2.12.** /spectcl/filter requests|chap7_2_filter]]
      13. [[**7.2.13.** /spectcl/fit requests|chap7_2_fit]]
      14. [[**7.2.14.** /spectcl/fold requests|chap7_2_fold]]
      15. [[**7.2.15.** /spectcl/integrate requests|chap7_2_integrate]]
      16. [[**7.2.16.** /spectcl/shmem requests|chap7_2_shmem]]
      17. [[**7.2.17.** /spectcl/sbind requests|chap7_2_sbind]]
      18. [[**7.2.18.** /spectcl/unbind requests|chap7_2_ubind]]
      19. [[**7.2.19.** /spectcl/mirror requests|chap7_2_mirror]]
      20. [[**7.2.20.** /spectcl/pman requests|chap7_2_pman]]
      21. [[**7.2.21.** /spectcl/project requests|chap7_2_project]]
      22. [[**7.2.22.** /spectcl/psuedo requests|chap7_2_pseudo]]
      23. [[**7.2.23.** /spectcl/rootree requests|chap7_2_roottree]]
      24. [[**7.2.24.** /spectcl/script requests|chap7_2_script]]
      25. [[**7.2.25.** /spectcl/treevariable requests|chap7_2_treevariable]]
      26. [[**7.2.26.** /spectcl/version requests|chap7_2_version]]
      27. [[**7.2.27.** /spectcl/exit requests|chap7_2_exit]]
      28. [[**7.2.28.** /spectcl/ringformat requests|chap7_2_ringformat]]
      29. [[**7.2.29.** /spectcl/specstats requests|chap7_2_specstats]]
      30. [[**7.2.30.** /spectcl/swrite requests|chap7_2_swrite]]
      31. [[**7.2.31.** /spectcl/sread requests|chap7_2_sread]]
      32. [[**7.2.32.** /spectcl/trace requests|chap7_2_trace]]
   4. [[**7.3.** Shared memory Mirror service|chap7_mirror]]
   5. [[**7.4.** Tcl REST reference|chap7_3]]
   6. [[**7.5.** Python REST reference|chap7_4]]
   7. [[**7.6.** Looking at the Rustogramer internals documentation|chap7_5]]
   8. [[**7.7.** Schema of configuration files|chap7_6]]
   9. [[**7.8.** Format of JSON Spectrum contents files|chap7_7]]
13. [[**8.** Appendix I - Installing Rustogramer|apppendix_1]]






 Track and set sidebar scroll position 

**


**

- Light
- Rust
- Coal
- Navy
- Ayu



**


# Rustogramer User Guide


[[**|print]]





 Apply ARIA attributes after the sidebar and the sidebar toggle button are added to the DOM 

# [Tcl REST interface](#tcl-rest-interface)


Two Tcl packages get installed with Rustogramer.


- On Windows these are installed in `%RUSTOGRAMER%\restclients\tcl` where `%RUSTOGRAMER%` is that directory you gaven to the installer.bat file.
- On Linux these are installed in `$dest/share/restclients/Tcl`  where `$dest` is the install directory you gave install.sh


These are ports of the SpecTcl REST client software and retain those names:


- SpecTclRESTClient is a package that provides low level REST request/response using the response formats created by both SpecTcl and Rustogramer.
- SpecTclRestCommand is a package that provides most of the Tcl command extensions that SpecTcl creates, however implemented over the REST interface.  This can be used as a tool to port existing SpecTcl Tcl/Tk based GUIs.


In addition, the program  `rusttcl.tcl` in that directory provides a script that you can use to run a Tcl shell that talks to rustogramer (well SpecTcl too for that matter).


## [Setting up the packages for use.](#setting-up-the-packages-for-use)


There are two ways to setup any Tcl package for use:


- Defining the environment variable `TCLLIBPATH` to include the directory tree that includes the package (e.g. /usr/opt/rustogramer/restclients/tcl on linux).
- Manually adding the package directory tree to the Tcl `auto_path` variable.


Suppose you have a script that defined the variable tclrest_dir to point to the directory that includes the Tcl Rest clients:


```tcl
lappend auto_path $tclrest_dir

```


will add those packages to the package search path used by the `package require` command.


How to create an environment variable depends on your environment.  This addition to your .bashrc can add $tclrest_dir to that variable in Linux:


```bash
export TCLIBPATH="$TCLLIBPATH $tclrest_dir

```


In Windows it's probably best to *very carefully* add this to the registery.  Start regedit and
navigate to `HKEY_CURRENT_USER\Environment`  Choose `Edit->New expandable string value`  Enter the name TCLLIBPATH and the value the path to your the restclients\tcl directory.


## [Using The low level client.](#using-the-low-level-client)


Once you are set up to add the package path for the Tcl REST clients to your scripts.  You can use the low leve client.  See the [[Tcl REST reference|./chap7_3]] for reference material.  In this section we're just going to give a brief overview of the package and how to use it.


The Tcl low level client is implemented in an object oriented manner.  You instantiate a client object and then issue it subcommands to get the server to do things.  It's important to note that the client does not attempt to connect with the server until it is asked to interact with it and each interaction, therefore involes a new connection to the server.


Here's a very brief example of how all this works.


```tcl
#    Somewhere above tclrest_dir was defined to point to the package directory.

lappend auto_path $tclrest_dir
package rquire SpecTclRESTClient;      # 1



set host locallhost;    # Modify if needed.
set port 8000;          # Modify if needed.         2
set debug 0;            # nonzero to enable debugging output.

set client [SpecTclRestClient %AUTO% -host $host -port $port -debug $debug]; # 3

# Let's see who we're talking to:

set versionInfo [$client version];   # 4

#  Major and minor and editlevel are always present. program_name was added last time:

if {[dict exists $versionInfo program_name]} {;     # 5
    set name [dict get $versionInfo program_name]
} else {
    set name *unknown*
}

set major [dict get $versionInfo major]
set minor [dict get $versionInfo minor]
set edit  [dict get $versionInfo editLevel];     # 6
puts "Connected to $name"
puts "Version $major.$minor-$edit"



```


Refer to the numbered comments above when reading the remarks below


1. Loads the Rest low level package.
2. These define the connection parameters for the client.  Note that the client can run in debugging mode, in which case, it output information about the requests it makes and the responses it got.  To run in debug mode set the `debug` variable to some non-zero value.
3. This creates a  client object using our connection parameters.  Note that the first paramter to the instance creation command is the name of a command ensemble that will be created (command ensembles are commands that have subcommands).  The special name `%AUTO%` will create a unique command name.  I recommned using `%AUTO%` to avoid colliding with other commands.  The name of the command is stored in the `client` variable.
4. This is the first (and  only) interaction with the server.  The `version` subcommand requests the server identify itself and its current version number.  The resulting information is stored in the dict `versionInfo`
5. Originally, when there was only SpecTcl, the only information returned was the major and minor versions and the edit lievel.  When rustogramer's Rest interface was written it, and later SpecTcl added the `program_name` key.  This block of code determines if the returned inforation has the `program_name` key and, if so, sets the value of `name` to it. Otherwise, the value of `name` is set to `*unknown*`
6. The version information is pulled out of the dict and finally everything is printed.


## [Using the high level client.](#using-the-high-level-client)


The high level client implements much of the SpecTcl command set on top of the
[low level Tcl REST client](#using-the-low-level-client).  To use it you must:


1. Pull the SpecTclRestCommand package into your script.
2. Provide the connection parameters to SpecTclRest package.
3. Use SpecTcl commands as you might normally do.


Here's a sample script to provide the version of the server and a list of the tree parameters and their metadata:


```tcl
...
#   some where above tclrest_dir is defined as the path to the package directory.

lappend auto_path $tlclrest_dir
package require SpecTclRestCommand

set host localhost
set port 8000

SpecTclRestCommand::initialize $host $port;   # 1

puts "SpecTcl/Rustogramer version [version]" ;  # 2


#   3

foreach param [treeparameter -list] {
    set name [lindex $param 0]
    set bins [lindex $param 1]
    set low  [lindex $param 2];         # 4
    set high [lindex $param 3]
    set units [lindex $param 5]

    puts "Name: $name  recommended axis: \[$low - $high\]$units $bins bins";  # 5
}

```


As before we assume that somewhere above the script shown, the script defines tclrest_dir to point to the package installation directory.


1. The `SpecTclRestCommand::initialize` command sets the connection parameters for the pacakge.  The parameters correspond in turn to the `-host` and `-port` option values to the constructor for the `SZpecTclRestClient` described in the [previous section](#using-the-low-level-client).
   Note that a third optional parameter, which defaults to `0` is used as the value for the `-debug` option.  This allows you to run the high level package with debugging output enabled on the low level package.
2. The `version` command in SpecTcl and the `SpecTclRestCommand` package provides the version of the histogramer.  This line simply outputs it.
3. The loop below iterates over the output of the `treeparameter -list` command.  This command, in SpecTcl and the `SpecTclRestCommand` package provides a list of information about parmeters and their metadata.  A REST endpoint is also defined for rustogramer that is identical to the one provided by SpecTcl that provides the same information for all parameters it knows about (you can think of all Rustogramer parameters as treeparameters in the SpecTcl sense of the word).
4. Each element of the list returned by `treeparameter -list` provides the following information:
   - The name of the parameter.
   - The number of bins recommended for axes on the parameter.
   - The suggested axis low limit for the parameter.
   - The suggested axis high limit for the parameter.
   - The width of an axis bin if the suggested limits and bin count are used.  We don't pull this out of the lst.
   - The units of measure for the parameter.
5. This line just outputs the information we extracted about the tree parameter.


The main point to take awayh from this example is that once you've pulled in the `SpecTclRestCommand` package and initialized it withthe connection parameters, you can treat your script as if it was running natively in SpecTcl (even if the server is Rustogramer) with the command descdribed in [the SpecTcl Command Reference](https://docs.nscl.msu.edu/daq/newsite/spectcl-5.0/cmdref/index.html) all defined.




 Mobile navigation buttons 
[[**|chapter_6]]
[[**|chap6_2]]



[[**|chapter_6]]
[[**|chap6_2]]









 Custom JS scripts
