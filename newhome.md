# What is NSCLDAQ?


NSCLDAQ is a software suite that provides a flexible and extensible
    framework for handling the data flow produced by nuclear physics
    experiments.  It aims to solve the top-level problem of managing the data
    stream by breaking it down into smaller problems solved by smaller
    applications. It therefore is a collection of tools that can be assembled
    into more complicated applications. This approach enables NSCLDAQ to be a
    modular system capable of tackling a wide range of experimental setups, from
    small calibration setups to merging multiple independent data acquisitions
    into unified systems.


As you can imagine, NSCLDAQ is a large package with many utilities. Indeed 
     a lot of time has been spent documenting its capabilities. For more 
     details, please continue reading the [user's 
     guide](https://github.com/FRIBDAQ/docs/tree/main/11.0/index.md) of the NSCLDAQ 11.0 comprehensive documentation. That should get 
     your feet wet.


[## Proceed to User's Guide](https://github.com/FRIBDAQ/docs/tree/main/11.0/index.md)


# What is SpecTcl?


SpecTcl is for analysis what NSCLDAQ is for dataflow. SpecTcl is a C++ 
      framework that allows experimenters to write custom analysis software that 
      seemlessly integrates with a histogramming engine and viewer.  SpecTcl
      enables the quick creation of histograms from the data and the ability to create
      1d and 2d gates and apply them to histograms on the fly.


[## Proceed to User's Guide](https://github.com/FRIBDAQ/docs/tree/main/../spectcl/index.md)
