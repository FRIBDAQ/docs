|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev |  | Next |


---

# <a name="chapter.security"></a>Chapter 50. Access control and security

Security consists of authentication, and authorization.
        Authentication determines who the entity requesting service is.
        Authorization determines if the authenticated entity has a right to
        request the service it has requested.

The NSCLDAQ security software helps your application to perform simple
        authentication and authorization according to policies set by your application.
        The NSCLDAQ security software is not a high security system.  It is
        primarily intended to avoid errors on multi users data taking systems.
        It is not intended to secure against malicious attacks.

The assumption is that your data acquisition system is already secured,
        from unauthorized users either by living behind a firewall, or by security
        management in the system itself.

Two class hierarchies work together to do authentication.  Authenticators,
        and Interactors.  Interactors accept authentication credentials from
        some source (credentials are anything that identify an entity within some
        authentication scheme).  Authenticators examine those credentials to determine
        if they are legitimate.

# <a name="AEN9720"></a>50.1. Incorporting the software into your code

In order to incorporate this software into your application you will
            need to include various header files.  The reference section for
            each class describes the headers you need.  The headers live in the
            include subdirectory of the nscldaq installation.
            Suppose you have an environment variable DAQROOT
            defined that points to the top level directory of the NSCL DAQ installation
            (at the NSCL, this is /usr/opt/daq/someversion where
            someversion is the version installed), to compile
            modules that include headers from this library you must:

<a name="AEN9727"></a>**Example 50-1. Compilation switches for the security includes**

```
g++ -c -I$DAQROOT/include ...
            
```

At link time, you must link the security library into your
            application.  To do this you must supply switches to help the
            linker locate the library at both link and run time, as the
            library is typically a shared library.  For example:

<a name="AEN9731"></a>**Example 50-2. Link switches for the security library**

```
g++ -o myapplication ... -L$DAQROOT/lib -lSecurity -Wl,"-rpath=$DAQROOT/lib"...
            
```

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Pointers to the reference material | Up | Authenticators |
