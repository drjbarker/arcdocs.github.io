# DLpoly

## Introduction

To access this software you need to be a member of the DLPOLY group, please submit a request to the research computing team via our [contact form](https://leeds.service-now.com/it?id=sc_cat_item&sys_id=7587b2530f675f00a82247ece1050eda) if you wish to be added to this group.

The licence terms are available on the [DLpoly license page](./dlpoly/license).

## Loading the module

When you log in, do:

```bash
$ module add dl_poly/4.05
```

To add the DLpoly executables to your environment.

## Batch execution

For the `dl_poly/4.05` module, the parallel executeable is `DLPOLY.Z.MPI` and serial executeable is `DLPOLY.Z.SRL1`.
For the `dlpoly/2.20` module, the parallel executable is `DLPOLY.X.parallel` and the serial executable is `DLPOLY.X`.

### Parallel execution

An example job submission script that calls DLpoly is shown below:

```bash
#$ -cwd -V
#$ -l h_rt=48:00:00
#$ -pe ib 16
mpirun DLPOLY.X.parallel
```

This requests 48 hours of runtime on 16 processes spread over Infiniband. It can be submitted with:

```bash
$ qsub dlpoly.sh
```

### Serial execution

The serial executeable is called `DLPOLY.X`, an example script `dlpoly_serial.sh` can be used to launch it:

```bash
#$ -cwd -V
#$ -l h_rt=48:00:00
DLPOLY.X
```

To submit the above script do:

```bash
$ qsub dlpoly_serial.sh
```
