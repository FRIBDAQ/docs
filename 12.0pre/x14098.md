|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 58. Shared memory | Next |


---

# <a name="shm_compile"></a>58.2. Compiling/Linking your software with the shared memory API

Compiling and linking a program that uses the `CDAQShm`
            class requires that you supply the correct -I
            switch so that the header file can be located.  It also
            requires that at link time you supply appropriate
            -L and -l switches to ensure
            that the library can be located and linked into the executable.

We also strongly recommend the use of an -rpath
            switch on the link line so that the shared library can be located
            at run-time without further environment variables.

The examples below assume that DAQHOME
            is an environment variable that points to the top of the
            NSLCDAQ 10.x or later installation tree.

<a name="AEN14109"></a>**Example 58-2. Compiling a C++ source that includes daqshm.h**

```
g++ -c  -I$DAQHOME/include mysource.cpp 
            
```

<a name="AEN14113"></a>**Example 58-3. Linking C++ object files that use the
            daqshm library**

```
g++ -o myprogram obj1.o obj2.o obj3.o -L$DAQHOME/lib -ldaqshm \
    -Wl,"-rpath=$DAQHOME/lib"
            
```

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Shared memory | Up | TheOsclass |
