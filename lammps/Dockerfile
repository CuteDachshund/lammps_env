FROM ubuntu:latest

RUN apt update && \
    apt upgrade -y
    
RUN apt install build-essential libopenmpi-dev -y

# lammpsをもってくる
RUN apt install git -y &&\
    git clone https://github.com/lammps/lammps.git 

RUN cd /lammps/src &&\
    make yes-MANYBODY &&\ 
    make yes-MOLECULE && \
    make mpi 
ENV PATH $PATH:/lammps/src


















