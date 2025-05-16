# Building-ECEarth3

Workflow for EC3

## Building

**Preliminary**

    cd /nobackup/rossby27/proj/optimesm/sm_renna/optimesm/sources
    #vi platform/nsc-tetralith-el9-intel-intelmpi.xml
    #vi environment.yml 
    #vi module_list.sh
    
    module load Mambaforge/23.3.1-1-hpc1 
    mamba create -n ecearth3 -f environment.yml  
    mamba env update -n ecearth3 -f environment.yml 

**Build Configuration**

    . module_list.sh 
    module load Mambaforge/23.3.1-1-hpc1 
    mamba activate ecearth
    util/ec-conf/ec-conf3 -p nsc-tetralith-el9-intel-intelmpi config-build.xml

**Compiling Oasis**

    cd oasis3-mct-5.2/util/make_dir/
    make -f Makefile.ece realclean
    make -f Makefile.ece pyoasis

**Compiling XIOS**

    cd xios-2.5/
    ./make_xios --arch ecconf --use_oasis oasis3_mct --netcdf_lib netcdf4_par  --job 6

**Compiling NEMO**

    cd nemo-3.6/CONFIG   
    ./makenemo -n ORCA1L75_LIM3_CarbonCycle -m ecconf -j6

**Compiling IFS**

    cd ifs-36r4
    make BUILD_ARCH=ecconf -j6 lib
    make BUILD_ARCH=ecconf master

**Compiling Runoff-mapper**
    
    cd runoff-mapper/src
    make

**Compiling ISM-mapper**

    cd ism-mapper/
    cmake

**Compiling LPJ-Guess**

    cd lpjg_v4p1/build/
    cmake ..
    make
    

**Compiling Pism**

    cd pism/build/
    cmake -C ../pism.nsc-tetralith-el9.cmake --fresh ..
    gmake -j 6 all
    

