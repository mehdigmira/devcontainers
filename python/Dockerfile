FROM mcr.microsoft.com/devcontainers/python:0.204.6-3.11-bullseye

# Necessary to install pyodbc.
RUN apt update && apt install unixodbc-dev --yes

# ML
RUN apt-get update && apt-get install -y wget gcc g++ gfortran libgfortran-9-dev liblapack-dev libamd2 libcholmod3 libmetis-dev libsuitesparse-dev libnauty2-dev git make pkgconf \
    && wget https://raw.githubusercontent.com/coin-or/coinbrew/master/coinbrew \
    && chmod a+x ./coinbrew \
    && ./coinbrew fetch Cbc@master --no-prompt \
    && mkdir -p /home/vscode/build/miplib \
    && ./coinbrew build Cbc@master --no-prompt --prefix=/home/vscode/build/miplib/ --tests=none --enable-cbc-parallel --enable-relocatable \
    && cd /home/vscode/build/miplib/lib && ln -s libCbc.so.0.0.0 libCbcSolver.so
