|  |  |  |
| --- | --- | --- |
| SpecTcl Command Reference. |
| Prev |  | Next |


---

# <a name="ref.swritecommand"></a>sread

<a name="AEN2908"></a>## Name

swrite -- Write spectrum contents to file.

<a name="AEN2911"></a>## Synopsis

**swrite `-format` *fmt file spec1 ?spec2 ... ?*
**

<a name="AEN2916"></a>## DESCRIPTION

Writes one or more spectra either to a file specified by name or a
            file opened with the Tcl open command.

Writes the spectra specified by
            `spec1`...
            `specn` to file.  The
            spectra are written in the order they are specified. The optional
            `-format` switch indicates that the next parameter
            specifies the file format.  The
            `file` parameter specifies the file to which
            the spectrum will be written.   The file parameter can be:



- A directory path to a file in which case the file is
                      created, written and closed.
- A file id returned from the Tcl open command in which case
                      the file id is written to in its current position and
                      remains open after the write.

<a name="AEN2929"></a>## OPTIONS

The `-format` option describes how the file will be
            written.  See the **sread** command for more information
            about the file formats.  THere are two formats (each has two
            names):



ascii, nsclasciiAn ASCII format.  Each spectrum consists of a header
                        and a set of lines containing channel coordinate/value
                        pairs for all nonzero channels in the spectrum.

binary nsclbinarySMAUG binary format.  This format is not recommended
                        unless you have old SMAUG analysis tools you intend to
                        use on the files.

<a name="AEN2947"></a>## EXAMPLES

<a name="AEN2949"></a>**Example 1. Writing spectra to file by filename**

```
swrite -format ascii somespectra.spc  raw.00 raw.01 raw02                
            
```

Three psectra are written to file into the file
            somespectra.spc.

<a name="AEN2954"></a>**Example 2. Writing to a file descriptor**

```
set fd [open "|gzip  > somespectra.gz" w]
swrite -format ascii $fd raw.00 raw.01 raw.02
            
```

The spectra are written to a pipeline created by the Tcl
            **open** command that compresses them using
            **gzip** into a file name somepsectra.gz.
            Note that the open command will require the spaces 
            before and after the
            output redirection character (>) unlike
            bash.

<a name="AEN2962"></a>## SEE ALSO



- [[r2174]]
- [[r2411]]
- **open**(3tcl)

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| version | Up | start |
