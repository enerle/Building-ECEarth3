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
    ...

**Compiling NEMO**
    ...

**Compiling IFS**
    ...

**Compiling Runoff-mapper**
    ...

**Compiling ISM-mapper**
    ...

**Compiling LPJ-Guess**
    ...

**Compiling Pysm**
    ...
    
nice
