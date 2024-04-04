# Use RHEL 8 as a base image
FROM registry.access.redhat.com/ubi8/ubi:latest

RUN dnf install -y gcc

# Install build dependencies
RUN dnf install -y \
    wget \
    tar \
    gcc \
    gcc-c++ \
    glibc-devel \
    make \
    bzip2 \
    zip \
    perl

# Download and extract GCC source
RUN wget https://ftp.gnu.org/gnu/gcc/gcc-13.2.0/gcc-13.2.0.tar.gz
RUN tar -xf gcc-13.2.0.tar.gz
RUN rm 	gcc-13.2.0.tar.gz

WORKDIR /gcc-13.2.0
RUN ls
# Build GCC
RUN ./contrib/download_prerequisites 
RUN mkdir build 
WORKDIR /gcc-13.2.0/build
RUN pwd
RUN ls ../
RUN ../configure --disable-multilib --enable-languages=c,c++ 
RUN dnf install -y diffutils

RUN make -j 12

RUN make install