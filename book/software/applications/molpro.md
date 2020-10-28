# Molpro

## Setting up the environment

To set up the environment load the version of the software that you want
to use. For example for version `2010.1.25` use:

    $ module add molpro/2010.1.25

## Scratch files

Molpro writes a larges amount of temporary or scratch files. By default
these are written to `/scratch` directory on compute nodes. The `/scratch` directories are usually fairly small and
may fill up quickly causing jobs to fail. In this case, to avoid these
failures you may need to change the location of the scratch files. You
can redirect these scratch files to your directory on the high speed
filesystem `/nobackup` ,
using the [-d] switch. For
example:

    molpro -d /nobackup/your_scratch_directory 

The directory `/nobackup/your_scratch_directory` is a directory that you create in the
`/nobackup` area. This is
most likely to be in your `/nobackup` area. Information about our `/nobackup` is available
<https://arc.leeds.ac.uk/using-the-systems/getting-started/nobackup/>.

It is best to use the version of molpro installed on the system as it is
installed and tested to run most efficiently but if you do choose to
install your own version of molpro you will need to configure it so that
it uses the `/scratch` area
or you should use the `-d $TMPDIR` or `-d /scratch` in your command line when you submit your job to the
batch system.

## Example job scripts

### Serial job submission

To run jobs through the batch scheduler, you need to submit them by
using the command `qsub <script name>` . The command to launch the serial version of molpro is
`molpro` . Below is an
example job script. The example script below requests 1Gb RAM for 2
hours, using the current environment and running from the current
working directory:

    #!/bin/bash
    #$ -l h_rt=2:0:0
    #$ -l h_vmem=1G
    #$ -V
    #$ -cwd
    molpro -d /nobackup/your_scratch_directory  