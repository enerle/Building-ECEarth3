# Building-ECEarth3

Workflow for EC3

## Building

**Compiling Oasis**

    cd /nobackup/rossby27/proj/optimesm/sm_renna/optimesm/sources
    . module_list.sh 
    module load Mambaforge/23.3.1-1-hpc1 
    mamba activate ecearth3
    
    ##util/ec-conf/ec-conf3 -p nsc-tetralith-el9-intel-intelmpi config-build.xml
    
    cd oasis3-mct-5.2/util/make_dir/
    make -f Makefile.ece realclean
    make -f Makefile.ece pyoasis

nice
