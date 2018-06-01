# FindSVSingularity
Singularity container for the FindSV pipeline. Use the following command to download the container

    singularity pull --name FindSV.img shub://J35P312/FindSVSingularity



# Contains

    TIDDIT

    SVDB

    Genmod

    Nextflow

    samtools

    python 2.7, including all modules for running FINDSV

# Usage
The environment is installed when running the FindSV install script. And the various package are run using FIndSV.

You may run any of the included packages manually:

    singularity exec samtools 

    singularity exec FindSV.simg genmod

    singularity exec FindSV.simg svdb

    singularity exec FindSV.simg python

    singularity exec FindSV.simg python /opt/TIDDIT/TIDDIT.py

# To be added
These modules still needs to be added
    
    CNVnator

    VEP

    manta

You need to install these modules yourself to run FindSV!
