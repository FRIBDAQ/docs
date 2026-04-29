|  |  |  |
| --- | --- | --- |
| Using NSCLDAQ with a CAEN V785 Peak-Sensing ADC and CAEN V262 IO Register |
| Prev | Chapter 3. Setting up the software | Next |


---

# <a name="AEN228"></a>3.3. Compiling the Readout program

Now that the source code for the Readout program is complete, 
              we need to compile it into an executable.

First, edit the Makefile supplied with the skeleton code so that
              it knows about your additional program files. Locate the line
              that reads:

```
Objects=Skeleton.o
            
```

and modify it so that it reads:

```
Objects=Skeleton.o MyEventSegment.o
            
```

Save this edit, exit the editor and type:

```
make
            
```

This will attempt to compile your readout software into an
              executable program called Readout. If the make command fails, fix
              the compilation errors indicated by it and retry until you get an
              error free compilation

---

|  |  |  |
| --- | --- | --- |
| Prev | Home | Next |
| Integrating your event segment with Readout | Up | The dumper program |
