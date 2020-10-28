# R

## Setting up the path and environment

All required environment variables can be set by loading the R module,
to do this issue:

    $ module add R

## Launching on the front end

R can be launched by entering its name at the command prompt; i.e.:

    $ R

Please note that this method should not be used apart from for quick
tests. Exit the R console by typing.

    q()

## Running through an interactive shell

The following will launch R interactively via the batch queues.

    $ qrsh -cwd -V -l h_rt= R 

The `<startup_flag>` can
be `--save` ,
`--no-save` or
`--vanilla` . I have used
--vanilla but information on the meaning of these flags can is
[here](https://stat.ethz.ch/R-manual/R-devel/library/base/html/Startup.html).
In the above command, is the length of real-time the shell will exist
for. e.g. to run R for 6 hours:

    $ qrsh -cwd -V -l h_rt=6:00:00 R --vanilla

This will run R from within the terminal from which it was launched.

## Batch Execution

To run R in batch-mode you must first generate a list of commands for R
to process in a file, e.g. [r.in]. You needed to make sure that this file is executable.
You can do this by running the command [chmod u+x .sh]. You can check this by running the command
[ls -la] command and the
information for that line will contain an x for execute like this
[-rwxr--r--].

A script must then be created that will request resources from the
queuing system and launch the R executable; script
[runR.sh] :

    #!/bin/bash
    # Run in current working directory and use current environment
    #$ -cwd -V
    # Set a 6 hour limit
    #$ -l h_rt=6:00:00
    #Request more memory, the default is 1Gb
    #$ -l h_vmem=1536M
    # Load R module
    module add R
    # run R using command file
    # CMD BATCH flag should be given to suppress graphics
    R CMD BATCH r.in r.out

This can be submitted to the queuing system using:

    $ qsub runR.sh

The files for a simple R test example are available to download in this
tar
file, [R.tar](https://arc.leeds.ac.uk/wp-content/uploads/2016/01/R.tar).

## Installing R packages

Given the large number of R packages available and pace of development,
it is preferable that users install the packages they need as opposed to
using a centrally provided set of packages.

### R 2.15.0 and later

To install package `foo` ,
start an R session by entering its name at the command prompt; i.e.:

    $ R

and then from within R, install the package:

    >install.packages('foo')

This will install the package and any dependencies that are required.
The package should then be accessible from subsequent R interactive
sessions and batch jobs.