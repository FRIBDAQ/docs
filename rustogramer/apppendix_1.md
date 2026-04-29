Provide site root to javascript 

 Work around some values being stored in localStorage wrapped in quotes 

 Set the theme before any content is loaded, prevents flash 


 Hide / unhide sidebar before it is displayed 


1. [[chapter_1]]
2. 1. [[chap1_1]]
3. [[chapter_2]]
4. 1. [[chap2_1]]
   2. [[chap2_2]]
5. [[chapter_3]]
6. [[chapter_4]]
7. 1. [[chap4_1]]
   2. [[chap4_2]]
   3. [[chap4_3]]
   4. [[chap4_4]]
   5. [[chap4_bindsets]]
   6. [[chap4_5]]
   7. [[chap4_6]]
   8. [[chap4_filters]]
   9. [[chap4_7]]
   10. [[chap4_8]]
8. [[chapter_5]]
9. [[chapter_6]]
10. 1. [[chap6_1]]
   2. [[chap6_2]]
11. [[chapter7]]
12. 1. [[chap7_1]]
   2. [[chap7_2]]
   3. 1. [[chap7_2_responses]]
      2. [[chap7_2_parameter]]
      3. [[chap7_2_rawparameter]]
      4. [[chap7_2_gates]]
      5. [[chap7_2_spectrum]]
      6. [[chap7_2_attach]]
      7. [[chap7_2_analyze]]
      8. [[chap7_2_apply]]
      9. [[chap7_2_ungate]]
      10. [[chap7_2_channel]]
      11. [[chap7_2_evbunpack]]
      12. [[chap7_2_filter]]
      13. [[chap7_2_fit]]
      14. [[chap7_2_fold]]
      15. [[chap7_2_integrate]]
      16. [[chap7_2_shmem]]
      17. [[chap7_2_sbind]]
      18. [[chap7_2_ubind]]
      19. [[chap7_2_mirror]]
      20. [[chap7_2_pman]]
      21. [[chap7_2_project]]
      22. [[chap7_2_pseudo]]
      23. [[chap7_2_roottree]]
      24. [[chap7_2_script]]
      25. [[chap7_2_treevariable]]
      26. [[chap7_2_version]]
      27. [[chap7_2_exit]]
      28. [[chap7_2_ringformat]]
      29. [[chap7_2_specstats]]
      30. [[chap7_2_swrite]]
      31. [[chap7_2_sread]]
      32. [[chap7_2_trace]]
   4. [[chap7_mirror]]
   5. [[chap7_3]]
   6. [[chap7_4]]
   7. [[chap7_5]]
   8. [[chap7_6]]
   9. [[chap7_7]]
13. [[apppendix_1]]






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


[[print]]





 Apply ARIA attributes after the sidebar and the sidebar toggle button are added to the DOM 

# [Appendix I - Installing Rustogramer](#appendix-i---installing-rustogramer)


Prior to version 1.1.1, you could only install Rustogramer from sources.  We will document that procedure, in case you want to do that as that option is still available.


With 1.1.1 and later a binary distribution was also made available.


## [Installation from source](#installation-from-source)


Installation from source requires the following:


- The Rust compilation environment.  The [Getting Started page](https://www.rust-lang.org/learn/get-started) of the Rust website descdribes how to do this and is our recommended way to get this.
- mdbook to build this user documentation.  Once the Rust compliation environment is installed you can install that using the command `cargo install mdbook`


### [Getting and building the program](#getting-and-building-the-program)


When you install from sources, you will need to download a release source from [the rustogramer git repository](https://github.com/FRIBDAQ/rustogrammer/releases).  If on windows, you should grab the .zip for the source code and if linux the .tar.gz.


After you have unwrapped the source code and set your working directory to the top level of the unwrapped distribution, you can build the debug and release versions of Rustogramer and user documentation using the same commands on windows and linux:


```bash
cargo build
cargo build --release
mdbook build docs

```


## [Doing the installation:](#doing-the-installation)


On linux you can run the shell script `deploy.sh` to install the package in some directory tree. On windows, you can use `install.bat` to do the same.  Both scripts require the same two command line parameters:  The version of Rustogramer (dev or release) you want installed and the destination directory.


#### [Final installation on Windows.](#final-installation-on-windows)


For example, on windows you might:


```cmd
.\install.bat release \rustogramer

```


to install the release version of rustogramer.  At the bottom of the output you'll get:


```
\rustogramer\rustogrammer will now run the histogramer.
\rustogramer\GUI   will now run the Python GUI
Point a web browser at:
\rustogramer\docs\user\index.html - for user Documentation      
\rustogramer\docs\internal\rustogramer\index.html - For internals documentation.
If you have installed CutiePie you can use it as a visualizer   
for you spectra.

```


If you want to install the debug version you can use e.g.:


```cmd
.\install.bat debug \rustogramer

```


#### [Final installation on Linux](#final-installation-on-linux)


For example on Linux you might:


```bash
./deploy.sh production /usr/opt/rustogramer/1.1.1

```


Or again to install the debug version:


```bash
./deply.sh debug /usr/opt/rustogramer/1.1.1

```


## [Installing from binaries.](#installing-from-binaries)


Beginning with release 1.1.1, the release products include files named:


- rustogramer-linux.tar.gz - Binary distribution for Linux
- rustogramer-widows.tar.gz  - Binary distribution for Windows (note that starting with windows 10, tar is included).


These are made with the scripts


```
make-linux-binary.sh

```


and


```
make-windows-binary.bat

```


in the source distribution.


To install from binaries


- Grab the distribution approprate to your system.
- Unwrap the tarball using tar xzf ....
- Follow the instructions in [Doing the installation](#doing-the-installation) above.




 Mobile navigation buttons 
[[chap7_7]]



[[chap7_7]]









 Custom JS scripts
