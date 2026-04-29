|  |  |  |
| --- | --- | --- |
| SpecTcl Command Reference. |
| Prev |  | Next |


---

# <a name="ref.stopcommand"></a>start

<a name="AEN3009"></a>## Name

stop -- stop analyzing data

<a name="AEN3012"></a>## Synopsis

**stop
            **

<a name="AEN3015"></a>## DESCRIPTION

Stops analyzing data fromt he current data source.  Data is no longer
            analyzed until the **start** command is next issued.
            Note that if you are using **ringselector** from
            NSCLDAQ as a pipe data source without the  `--non-blocking`
            option, this will eventually cause data acquisition to halt with
            backpressure.  We therefore strongly encourage the use of the
            `--non-blocking` option with
            **ringselector**.

<a name="AEN3023"></a>## SEE ALSO



- [[r2974]]
- [[r102]]

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| start | Up | rootexec |
