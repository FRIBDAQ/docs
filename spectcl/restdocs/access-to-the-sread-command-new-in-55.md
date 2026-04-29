|  |  |  |
| --- | --- | --- |
| SpecTcl REST plugin |
| Prev | Chapter 3. REST requests supported. | Next |


---

# <a name="AEN1491"></a>3.21. Access to the sread command (new in 5.5)

The **sread** command supports reading spectra
                from file. This is done using the following URL form

<a name="AEN1495"></a>**http://host:port/spectcl/sread?filename=fname[&format=fmt&snapshot=flag&replace=flag&bind=flag]
                   **

With the exception of filename, the
                query parameters are all optional:



filenameName of the file to be read.  note that the filename
                        will be interpreted by SpecTcl not the client.

formatFormat of the file.  This defaults to
                        ascii  which is the best format.

snapshotBy default this is 1.  If true, the resulting spectrum
                        will be a snapshot spectrum.  That is it will not be
                        hooked to the increment logic of SpecTcl. If false,
                        (0), future events can increment the resulting spectrum.

replaceBy default this is 0.  If true (1), the spectrum
                        read in will replace any spectrum that already exists with
                        the name of the spectrum in the file.  Otherwise, if necesary,
                        a new unique spectrum name will be assigned to the
                        new spectrum.

bindBy default this is 1, which binds the spectrum into the
                        displayer shared memory region.  If 0, the spectrum
                        will not be bound to the displayer.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Accessing the pseudo command (new in 5.5) | Up | Access the ringformat command (new in 5.5) |
