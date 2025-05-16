# Building-ECEarth3

Workflow for EC3

## Building

**Build Configuration**

    cd /nobackup/rossby27/proj/optimesm/sm_renna/optimesm/sources
    . module_list.sh 
    module load Mambaforge/23.3.1-1-hpc1 
    mamba activate ecearth
    util/ec-conf/ec-conf3 -p nsc-tetralith-el9-intel-intelmpi config-build.xml

**Compiling Oasis**

    cd oasis3-mct-5.2/util/make_dir/
    make -f Makefile.ece realclean
    make -f Makefile.ece pyoasis

**Compiling XIOS**

    dummy

**Compiling NEMO**

    dummy

**Compiling IFS**

    dummy

**Compiling Runoff-mapper**

    dummy

**Compiling ISM-mapper**

    dummy

**Compiling LPJ-Guess**

    dummy

**Compiling Pysm**

    dummy
    
nice
