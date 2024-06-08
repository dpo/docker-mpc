FROM ubuntu:24.10
LABEL maintainer="dominique.orban@gmail.com" 
RUN  apt-get -y update && apt-get -y install curl

## gcc/g++/gfortran
RUN  apt-get install -y gcc-13 g++-13 gfortran-13

# juliaup (which installs Julia)
RUN  curl -fsSL https://install.julialang.org | sh -s -- -y

# to avoid interactive dialog about timezones
RUN  DEBIAN_FRONTEND=noninteractive apt-get -y install tzdata

# Python
RUN  apt-get install -y python3 pip

# tools
RUN  apt-get install -y git make cmake autoconf tmux

# editors
RUN  apt-get install -y vim
# RUN  apt-get install -y emacs

# prompt
COPY .mpc_prompt.sh /
RUN  cat /.mpc_prompt.sh >> /root/.bashrc

# project README
COPY PAPER_README.txt /
