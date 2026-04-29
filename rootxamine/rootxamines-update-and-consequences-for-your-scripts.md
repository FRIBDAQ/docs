|  |  |  |
| --- | --- | --- |
| Rootxamine - Attaching CERN Root to SpecTcl's Spectrum Shared Memory |
| Prev |  |  |


---

# <a name="ch.update"></a>Chapter 3. rootxamine's update and consequences for your scripts.

This chapter describes how **rootxamine** works
        and soeme of the consequences this has for user code.

When **rootxamine** runs, it creates a recurring
        `TTimer` derived object with a one second
        period.  The `Notify` method if this object
        maintains a set of Root histograms in the /
        directory that correspond to those in the SpecTcl shared memory it
        is mapped to.

The histogram objects are ordinary Root `TH1`
        derived objects but the `fArray` and
        `fN` data members
        of the underlying histogram data are tampered with at creation time
        to point into the mapped shared memory.
        This is possible because  `TH1` is derived
        from a `TArray` and those data attributes
        are public.

The immediate consequences of this choice are both positive and
        negative:



- On the plus side, there's never any expensive bulk data
                movement from the shared memory into the histogram's memory,
                this is not compute intensive.
- On the minus side, the spectrum channel data are read-only
                because that's how the shared memory is mapped.
- Since the contents of the histograms did not get there
                via calls to the `Fill` method,
                Statistics kept by `THxx` `Fill`
                methods are not kept.
  You can use the `ResetStats` method
              of `TH1` to compute those statistics
              from the contents of the histogram  however note that
              these statistics will not update as the spectrum contents change
              and that depending on the size of the spectrum, this can
              be an expensive operation.  This is why we don't do this as
              part of our housekeeping operations.

Maintaining histograms means looking at entries in the Xamine
        shared memory and:



- If a previously unused spectrum slot becomes used,
                creating a new Root histogram that corresponds to that.
- If a previously used spectrum slot becomes unused,
                deleting the existing Root histogram object that
                jacketed that spectrum.
- If the spectrum in a previously used slot changes,
                The existing Root histogram object that represents the old
                spectrum is deleted and a new one representing the new
                spectrum is created.
  At this point in time, *changed* means
              that any of the following is true:
  - The spectrum type has changed.
  - The spectrum dimensions have changed.
  - The spectrum axis specifications have changed.

This update algorithm means that if you create a pointer to
        a spectrum you need to know if that pointer is still valid.
        Unfortunately there is no way to know that at present.
        Here's an example.  Suppose we have a spectrum named
        "myspectrum" that we know is a 1-d long spectrum.  We can get a pointer to
        that histogram in a Root script as follows:

<a name="AEN220"></a>```
TH1I* pSpectrum = (TH1I*)(gDirectory->FindObject("myspectrum"));
        
```

Suppose at some later time, that spectrum is removed from shared
        memory or the spectrum in its slot is replaced with a different
        spectrum.  The following, seemingly innocuous code will segfault:

<a name="AEN223"></a>```
pSpectrum->Draw();
        
```

As will, even

<a name="AEN226"></a>```
delete pSpectrum;               // Double delete.            
        
```

You might think I could tell you if a pointer pointed to
        a currently maintained histogram and you'd be right but even that
        can fail as follows due to the inherent asynchronism between the
        rootxamine and the SpecTcl program maintaining the shared memory
        contents:

<a name="AEN229"></a>```
TH1I* pSpectrum = (TH1I*)(gDirectory->FindObject("myspectrum"));
if (isMaintained(pSpectrom)) {
   pSpectrum->Draw();  
}
        
```

In the code above if after the hypothetical `isMaintained`
        is called, the spectrum is killed off by SpecTcl before or during
        the execution of the `Draw` method
        the segfault will still occur.  Therefore we don't bother to
        give the illusion of safety.

Fortunately in most cases the spectrum definitions in
        the shared memory are relatively stable.  Furthermore, starting up
        **rootxamine** is relatively cheap.

Finally,  If you use `TBrowser`, you'll find the
        spectra created in /root/ROOT Memory.
        Sadly, `TBrowser`'s listing of objects on the
        left side is *static*.  This means that:



- Updating won't  reflect any spectra added to the shared memory.
- Even worse, updating won't reflect any spectra that
                were
                removed from shared memory which allows you to quite happily
                double click on a deleted spectrum to 'display it' and
                make Root segfault
- Replacing a spectrum is the same as above.  The name
                evidently has, associated with it, a static pointer to the
                named object that is not updated and, again, referencing it
                will cause a segfault.

The only thing you can do is destroy the browser and
        start a new one.  It will query the set of objects anew
        and reflect all changes to the SpecTcl shared display memory.

One final caution.  If your
        SpecTcl reads a SpecTcl configuration file that
        matches the current configuration, you might think you're in good shape.
        In fact you are not.  Reading a SpecTcl configuration file means
        destroying all spectra and creating the ones described in the
        configuration file, then binding them into the display memory.
        In this process, spectra could be mapped to different slots, or
        their contents could move around in the shared memory or,
        if the update process runs between the time all spectra are destroyed
        and all spectra have been rebound into the display memory
        any histogram pointers you have are bad.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home |  |
| How to run xamineroot |  |  |
