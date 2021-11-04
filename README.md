# OpenFOAM2.4.0-HPC
install OpenFOAM2.4.0 in HPC (tips and log files)
https://openfoamwiki.net/index.php/Installation/Linux/OpenFOAM-2.4.0/CentOS_SL_RHEL
### set environment
module load mpich/3.2/INTEL-18.0.0
### change OpenFOAM-2.4.0/etc/bashrc
please take the bashrc file as a reference
1. foamInstall=/project/cs16/tma5/$WM_PROJECT
2. export WM_MPLIB= INTELMPI
3. export WM_PROJECT_USER_DIR=/project/cs16/tma5/$WM_PROJECT/$USER-$WM_PROJECT_VERSION


### change OpenFOAM-2.4.0/etc/config/setting.sh
please take the setting.sh file as a reference
1. gcc_version=gcc-4.8.4
2. export MPI_ROOT="/usr/local/packages/mpich/3.2/INTEL-18.0.0/"

### echo 
alias of240='source /project/cs16/tma5/OpenFOAM/OpenFOAM-2.4.0/etc/bashrc WM_NCOMPPROCS=4 foamCompiler=ThirdParty WM_COMPILER=Gcc48 WM_MPLIB=SYSTEMOPENMPI'

### any problem if encontored can refer to log.make file to see the details

### ThirdParty
The following files should be checked(not changed by hand, should be changed automatically)
1. makeCGAL
boostPACKAGE=boost-system -> boostPACKAGE=boost_1_54_0
${0##*/} boost-system gmp-system -> ${0##*/} boost_1_54_0 gmp-system
2. makeGcc
--with-system-zlib \ -> --with-system-zlib --disable-multilib \
If encoutered any problem, please refer to the log files(log.mkbinutils; log.mkcgal; log.mkcmake; log.mkgcc)

### usage in the HPC
```bash
module load gcc/8.4.0
source /project/cs16/tma5/OpenFOAM/OpenFOAM-2.4.0/etc/bashrc WM_NCOMPPROCS=4 foamCompiler=ThirdParty WM_COMPILER=Gcc48 WM_MPLIB=SYSTEMOPENMPI
```
