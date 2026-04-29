|  |  |  |
| --- | --- | --- |
| Batch SpecTcl (5.2 and later) |
| Prev | Chapter 4. MPISpecTcl - Massively parallel SpecTcl. | Next |


---

# <a name="AEN570"></a>4.2. Parallel models for SpecTcl

This section will consider two parallel models for SpecTcl.
                In both models, the worker processes analyze work items
                sent by the rank 0 process and, at the end of analysis,
                are queried for their spectra.

The model we will consider in the next chapter uses work units that are a
                single block of complete ring items.  In that model, the rank
                0 process has a file data getter, and an mpidistributor while all
                other processes have an mpi data getter and an analyzer distributor.

Each block of data is distributed to the next requestor.  Each
                process that is not rank 0 is given the entire configuration
                file and independently histograms.  When analysis is completed,
                spectra are gathered from the non rank 0 workers and summed into the
                rank 0 process from which they can be written.

This model should scale linearly until I/O limitations bottleneck
                the computation.  Note that included in the I/O limitations are
                file read performance and communication costs between the
                workers and the rank 0 process.  This process is, most often,
                suitable.  We'll call this model
                *serial I/O parallel computation*

If the files to be analyzed are scattered across multiple
                servers, parallel I/O can be performed.  This model
                *Parallel I/O parallel computation* can be
                implemented without using the additional getter/distributors in
                the mpispectcl package.  It should scale up
                to the aggregate I/O bandwidth.

In this second model, all non rank 0 processes are independent
                batch Spectcls with the exception that the rank 0 process
                feeds each of them a set of files to analyze.

Since traffic shaping is important, each worker might be given
                a set of files that are on one server.  The files are serially
                analyzed by each non rank 0 process and, when each process is done,
                it notifies the rank 0 process which collects the spectra from
                that process summing it into the spectra it has.   When all workers
                are done, the rank 0 process can save spectra.

This model has more limited application as it requires data to
                be distributed in some manner on the network.  It is possible
                and relatively simple to implement.

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| MPISpecTcl - Massively parallel SpecTcl. | Up | Serial reader parallel worker example. |
