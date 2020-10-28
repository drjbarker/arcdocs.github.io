# NAMD

## License Arrangements

This software is installed with a non-commercial use license. Access to
this software is restricted. User must agree to the license, found
[here](http://www.ks.uiuc.edu/Research/namd/license.html). Please send a
written statement accepting the license terms as a ticket to the
Research Computing Team (<https://bit.ly/arc-help>) in order for us to
give you access to NAMD.

## Example submission script

An example script, `namdexample.sh` , looks like:

    #!/bin/bash
    #$ -pe ib 8
    #$ -l h_rt=12:0:0
    #$ -l h_vmem=1G
    #$ -cwd

    module add namd/2.9
    mpirun namd2 name_of_config_file.conf > output_log_file.log

This example requests 8 cores for 12 hours, with each core limited to
1Gb of RAM. It assumes that you are submitting the job from the
directory containing your input files.

**Note**: prior to NAMD 2.9, the `namd2` binary was called `namd2.MPI` .