
# DLpoly

## Introduction

To access this software you need to be a member of the DLPOLY group,
please contact <arc-help@lists.leeds.ac.uk> if you wish to be added to
this group.

The licence terms are available through [this
link](https://arc.leeds.ac.uk/software/applications/dlpoly/dlpoly-licence-conditions/).

## Setting the module environment

When you log in, do:

    $ module add dl_poly/4.05

To add the executables to your environment.

## Batch execution

For the `dl\_poly/4.05`
module, parallel ( `DLPOLY.Z.MPI` ) and serial ( `DLPOLY.Z.SRL1` ) executables are available on the system.
For the `dlpoly/2.20` module
the parallel executable is `DLPOLY.X.parallel` and the serial executable is
`DLPOLY.X` .

### Parallel execution

An example script, `dlpoly.sh` , looks like:

    #$ -cwd -V 
    #$ -l h_rt=48:00:00
    #$ -pe ib 16
    mpirun DLPOLY.X.parallel 

This requests 48 hours of runtime on 16 processes. It can be submitted
with:

    $ qsub dlpoly.sh

### Serial execution

The serial code is called DLPOLY.X, an example script
`dlpoly\_serial.sh` can be
used to launch it:

    #$ -cwd -V 
    #$ -l h_rt=48:00:00
    DLPOLY.X 

To submit the above script do:

    % qsub dlpoly_serial.sh 