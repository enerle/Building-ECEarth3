# Building-ECEarth3

Workflow for EC3

## Building

**Preliminary**

Get code 

    svn checkout https://svn.ec-earth.org/ecearth3/branches/projects/optimesm

Move here

    cd /sources

Modify 

    platform/nsc-tetralith-el9-intel-intelmpi.xml

Create

    touch module_list.sh

where we call the next modules

    module purge
    ml Mambaforge/23.3.1-1-hpc1
    ml buildenv-intel/2023a-eb
    ml netCDF-HDF5/4.9.2-1.12.2-hpc1
    ml eccodes/2.32.0-ENABLE-AEC-hpc1
    ml CDO/2.3.0-eccodes-aec-cmor-hpc1-intel-2023a-eb
    ml UDUNITS2/2.2.28-hpc1-intel-2023a-eb
    ml GSL/2.7.1-hpc1
    ml PETSc/3.17.4-hpc1
    ml NCO/4.7.9-nsc5-intel-2018a-eb

Then we create the Python environment in Mambaforge (locate ../)

    module load Mambaforge/23.3.1-1-hpc1 
    mamba create -n ecearth3 -f environment.yml  
    mamba env update -n ecearth3 -f environment.yml 

**Build Configuration**

We load the environment and required modules

    . module_list.sh 
    module load Mambaforge/23.3.1-1-hpc1 
    mamba activate ecearth

Run configuration file
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


**Not documented**

1. We need to create an environment setting numpy <2
2. eccodes missing GRIB table


    cd pism/build/
    cmake -C ../pism.nsc-tetralith-el9.cmake --fresh ..
    gmake -j 6 all
   

    cd sources/util/grib_table_126
    mamba activate ecearth3
    ./define_table_126.sh 




    

