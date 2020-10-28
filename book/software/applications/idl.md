# IDL 

IDL is a data analysis programming language. Only authorised users can
use IDL.

[Vendor Website](http://www.exelisvis.co.uk/ProductsServices/IDL.aspx)

## Getting started

In order to use IDL on the ARC clusters, you will need to contact your
department for licence server information. This will normally be
provided as a `port` and a
`machine name` in the format:

    port@machine

You will need to set the `LM\LICENSE\FILE` environment variable before you use IDL:

    export LM_LICENSE_FILE=port@machine:$LM_LICENSE_FILE

After that, you should be able to load the IDL module:

    module load idl

and then run the application by entering the command `idl`

## Running IDL as a batch job

A suitable script to run an IDL program as a batch job with no
interaction is:

    #$ -V -cwd
    #$ -l h_rt=6:00:00
    #$ -l h_vmem=1G

    module load idl
    idl 

This will run the application:

-   from your current directory with the currently loaded module
    environment
-   with 6 hours of run-time
-   requesting 1GByte of memory

If this is saved as a text file with the name:
`idl\script.sh` it can then
be submitted with:

    qsub idl_script.sh

## Running IDL as an interactive job on the compute nodes

IDL can also be launched as an interactive job on the back-end compute
nodes through `qrsh` :

    export LM_LICENSE_FILE=port@machine:$LM_LICENSE_FILE
    module load idl
    qrsh -cwd -V -l h_rt=6:00:00,h_vmem=1G -pty y $IDL_HOME/idl/bin/idl

This will request 1 cpu for 6 hours, with 1G of RAM.

Not that if the resources are not available at the point the scheduler
tries to allocate them, then the request will fail.

You may find you have to submit the request a few times until it is
successful.