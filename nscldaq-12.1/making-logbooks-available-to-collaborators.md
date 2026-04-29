|  |  |  |
| --- | --- | --- |
| NSCL DAQ Software Documentation |
| Prev | Chapter 24. NSCLDAQ Logbook facility | Next |


---

# <a name="sec.lg_export"></a>24.4. Making logbooks available to collaborators

This chapter will describe how to export a logbook for use outside
         of the NSCL.  While the logbook is a simple file and can easily
         be copied anywhere, you also need the logbook software in order to
         use it.

This section will describe how to use the NSCL linux containers
         to install NSCLDAQ so that you can use the logbook facility with
         minimal hassle.  You will need a linux computer at your home institution
         that can run the singularityc container system.

The remainder of this chapter will:



- Describe how to obtain and the NSCL-linux singularity container.
- How to get the NSCLDAQ binary distribution you need
- How to install the container and NSCLDAQ binary installtion
                 tree on your system
- How to run the singularity container so that you can
                 use the logbook system.

## <a name="AEN9872"></a>24.4.1. Obtaining a suitable NSCL-linux container

First a bit about what a container image is and what singularity is.

Container technology provides a light-weight scheme for executing
            user land software for one distribution of linux on the run-time
            environment of another distribution.  For example, At the NSCL,
            we use and have established reasonable methods for installing our software
            on Debian systems.  Your institution may run a Red Hat Enterprise
            Linux base distribution such as CentOS.  The names and availablility
            of packages needed to support NSCLDAQ may differ.

Rather than trying to figure out how to install NSCLDAQ on all Linux
            distributions, wouldn't it be nice if you could run a simple program
            and your filesystem containing the Linux userland programs and libraries
            would be Debian?  This is what singularity container images provide.

A singularity container image can be thought of as a part of a filesystem
            that gets overlaid on top of the running Linux system filesystem
            while you are running that container.  This allows us to provide
            you with a Debian environment that you can run on your e.g. CentOS
            environment.  Because singularity containers only play games with what
            the filesystem look like, the overhead for running a container is
            essentially nonexistent once a program starts.

What you *will* need, however is the singularity
            container run-time environment.  For Debian like systems (e.g.
            Ubuntu, Kubuntu etc.), this is provided by the singularity-container
            package.  For RHEL based systems **yum** can be used
            to install the singularity package.  For
            general installation instructions that can be used to guide you through
            other linux distributions, see the singularity Admin guide for the
            appropriate version of singularity at
            [https://sylabs.io/docs/](https://sylabs.io/docs/).

In order to keep our singularity image small, and to avoid re-making
            it for each NSCLDAQ or SpecTcl update (you can use Singularity to also
            install SpecTcl), our images only contain the linux packages needed
            to support our software and we use filesystem binding to keep
            our container images separate from the actual software installation
            trees.  This is why you need to get both an image and a corresponding
            binary installation tree.

Our images are installed at the NSCL in /usr/opt
            with names like nscl-*code-word*.img
            where *code-word* is the linux distribution
            code-word.  For example, as I'm writing this, we have two images:
            /usr/opt/nscl-jessie.img which provides
            a Debian-8 (jessie) environment and
            /usr/opt/nscl-buster.img which  provides
            a Debian-10 (buster) environment.

At NSCL/FRIB your experiment will, in general run in a container.
            For simplicity, choose the container you used for your experiment,
            and copy it to your institution.  While 'large', the images are not
            enormous clocking in at about 2GB for the buster image.

## <a name="AEN9893"></a>24.4.2. Getting the NSCLDAQ binary distribution

The simplest way to get this is to run the container you used
            for your experiment in the same way you ran it during the experiment.
            When you do, the evironment variable DAQROOT
            will point to the installation tree you'll need to grab.

The following creates a *tarball* of that
            directory tree in your home directory:

<a name="AEN9899"></a>```
cd $DAQROOT
tar czf ~/nscldaq-install.tar.gz .
            
```

Pull the resulting tarball, ~/nscldaq-install.tar.gz
            over to your home institution.  The resulting tarball should be
            smaller than 200Mbytes.  Also make note of the value of the
            DAQROOT
            environment variable.  You'll need it later.

## <a name="AEN9904"></a>24.4.3. Installing your container and NSCLDAQ tree.

So you've got a container and a tarball of an NSCLDAQ installation
            tree.  You need to put the container image somewhere and
            unroll the nscldaq-install.tar.gz tarball
            somewhere where it's easy to coerce singularity to map that directory
            tree back to its original position in the directory tree.

To do this, I'm going to assume you have some directory somewhere
            for simplicity, we'll call it /nscldaqinstall
            modify these instructions to match where you actually put this stuff.
            Note that centralizing this installation will allow anybody with read
            access to the container and the NSCLDAQ directory tree to use
            its software.

first put your container (for simplicity I'm going to assume you
            grabbed nscl-buster.img) in
            /nscldaqinstall/nscl-buster.img.

Next unwrap the tarball as follows (I'm going to assume DAQROOT claimed)
            it was /usr/opt/nscldaq/12.0-000), and that the
            tarball is now sitting in your home directory.

<a name="AEN9915"></a>```
mkdir /nscldaqinstall/opt-buster       # in case later you get a second container.
mkdir -p /nscldaqinstall/opt-buster/nscldaq/12.0-000  # We'll put tuff here.
(cd /nscldaqinstall/opt-buster; ln nscldaq daq);   # NSCL has this convenience link.
(cd /nscldaqinstall/opt-buster/nscldaq/12.0-000; tar xzf ~/nscldaq-install.tar.gz)

            
```

Ok, let's review what we've done and why. First we installed
            our container where we can get it.  Second we produced a directory tree
            that can be mapped on to /usr/opt in the container that mimics what
            NSCL does and put the contents of our tarball in the correct part of
            that directory tree.  If we wanted to haul SpecTcl 5.3-010 over, for example,
            we'd just need to add /nscldaq/opt-buster/spectcl/5.3-010
            grab a tarball as we did for NSCLDQAQ and unwrap it there.  Similarly
            if we need additional versions of NSCLDAQ or spectcl we can grab
            additional tarballs and drop them in appropriate parts of the
            /nscldaqinstall/opt-buster directory tree.
            We could even grab the installation of root in /usr/opt from NSCL
            and drop that in (we'd need that for SpecTcl and we might just want
            it in the container after all).

## <a name="AEN9920"></a>24.4.4. Running the singularity container

Now we're ready to get going. We're going to use the
            **singularity** command to overlay the
            filesystem in the container image we grabbed onto our linux userland
            filesystem and overlay, or in singularity terms *bind*
/nscldaqinstall/opt-buster into /usr/opt
            in the container.

Here's the singularity command to so so (assuming you grabbed
            nscl-buster.img):

<a name="AEN9928"></a>```
singularity shell --bind /nscldaqinstall/opt-buster:/usr/opt \
   /nscldaqinstall/nscl-buster.img
            
```

If you do this you should wind up with a shell and prompt that looks like:
            Singularity nscl-buster.img:~> indicating you're
            executing inside the singularity container. Some things to note:



- Your home directory tree is available where it normally is.
- Your current default directory tree at the time you
                    started singularity is available as your
                    current default directory
- /usr/opt/daq, or
                    /usr/opt/nscldaq
                    should contain the
                    NSCLDAQ installation directory tree you pulled over from the
                    NSCL and you can e.g.
                    **. /usr/opt/daq/12.0-000/daqsetup.bash**
                    to setup  the full set of NSCLDAQ environment variables will
                    be created.

When you start a container,  you can specify additional bindings
            from your host filesystem into your container.  bindports have the
            form source[:dest] where source
            is where the directory tree being bound is located in the host filesystem
            and the optional dest is where that directory tree
            should appear in the container filesystem.  If the destination
            is not supplied, the source is bound to the same location it appears
            in the host.

Suppose, for example, you have a directory tree; /projects
            you want to appear as /projects you can start
            the container as:

<a name="AEN9949"></a>```
singularity shell --bind /nscldaqinstall/opt-buster:/usr/opt,/projects \
   /nscldaqinstall/nscl-buster.img
               
            
```

To make this happen.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Using the logbook in an experiment | Up |  |
