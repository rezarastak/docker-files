FROM dealii/base:gcc-mpi

MAINTAINER timo.heister@gmail.com

USER root
RUN apt-get update && apt-get -yq install \
    gmsh

ADD candi/ $HOME/candi/
RUN chown -R $USER:$USER $HOME/candi/
USER $USER

RUN \
  cd candi && \
  ./candi.sh -j4 \
	--platform=deal.II-toolchain/platforms/supported/ubuntu16.platform \
	--prefix=$HOME/libs \
	--packages="load:dealii-prepare once:arpack-ng once:opencascade once:parmetis once:superlu_dist once:hdf5 once:p4est once:trilinos once:petsc once:slepc once:assimp once:nanoflann once:sundials once:adolc" &&\
  rm -rf $HOME/candi $HOME/libs/tmp

# I don't know how to import env vars from the configuration folder.  This
# probably doesn't work at all, because we don't use bash but sh and so we can
# not use 'source' or any of the bash startup files. Manually export the paths
# here instead:
RUN cat ~/libs/configuration/* | grep export | sort

ENV ADOLC_DIR=/home/dealii/libs/adolc-2.6.4-rc1
ENV ARPACK_DIR=/home/dealii/libs/arpack-ng-3.6.2
ENV ASSIMP_DIR=/home/dealii/libs/assimp-3.3.1
ENV HDF5_DIR=/home/dealii/libs/hdf5-1.10.1
ENV METIS_DIR=/home/dealii/libs/parmetis-4.0.3
ENV NANOFLANN_DIR=/home/dealii/libs/nanoflann-v1.2.3
ENV OPENCASCADE_DIR=/home/dealii/libs/oce-OCE-0.18.2
ENV P4EST_DIR=/home/dealii/libs/p4est-2.0
ENV PARMETIS_DIR=/home/dealii/libs/parmetis-4.0.3
ENV PETSC_DIR=/home/dealii/libs/petsc-3.7.6
ENV SLEPC_DIR=/home/dealii/libs/slepc-3.7.3
ENV SUNDIALS_DIR=/home/dealii/libs/sundials-3.1.0
ENV SUPERLU_DIR=/home/dealii/libs/superlu_dist_5.1.2
ENV TRILINOS_DIR=/home/dealii/libs/trilinos-release-12-10-1
ENV SCALAPACK_DIR=/home/dealii/libs/petsc-3.7.6
