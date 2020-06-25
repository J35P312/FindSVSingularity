Bootstrap: docker
From: ubuntu:16.04

%environment
SHELL=/bin/bash
PATH=/opt/anaconda/bin:${PATH}
LC_ALL=C.UTF-8
ROOTSYS=/opt/root/
LD_LIBRARY_PATH=/opt/root/lib


%runscript
    echo "This is what happens when you run the container..."
    export PATH=/opt/anaconda/bin:${PATH}

%post
    echo "Hello from inside the container"
    apt-get update
    apt-get -y install wget git bzip2 build-essential gcc zlib1g-dev language-pack-en-base apt-transport-https make cmake unzip libncurses5-dev libncursesw5-dev
    update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8

    cd /root/ && wget https://repo.continuum.io/miniconda/Miniconda2-latest-Linux-x86_64.sh
    cd /root/ && chmod 700 ./Miniconda2-latest-Linux-x86_64.sh
    cd /root/ && bash ./Miniconda2-latest-Linux-x86_64.sh -b -p /opt/anaconda/   

    export PATH=/opt/anaconda/bin:${PATH} 

    cd /opt/ && wget https://root.cern.ch/download/root_v6.13.02.Linux-ubuntu16-x86_64-gcc5.4.tar.gz
    cd /opt/ && tar -xvf root_v6.13.02.Linux-ubuntu16-x86_64-gcc5.4.tar.gz

    export ROOTSYS=/opt/root
    export PATH=$PATH:$ROOTSYS/bin
    export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$ROOTSYS/lib

    cd /opt/ && wget https://github.com/abyzovlab/CNVnator/releases/download/v0.3.3/CNVnator_v0.3.3.zip
    cd /opt && unzip CNVnator_v0.3.3.zip
    cd /opt/CNVnator_v0.3.3/src/samtools/ && make
    cd /opt/CNVnator_v0.3.3/src/ && make

    cd /opt/ && wget https://github.com/SciLifeLab/TIDDIT/archive/TIDDIT-2.8.0.zip && unzip TIDDIT-2.8.0.zip
    mv /opt/TIDDIT-TIDDIT-2.8.0 /opt/TIDDIT
    cd /opt/TIDDIT && ./INSTALL.sh .

    cd /opt/ && git clone https://github.com/J35P312/SVDB.git  
    cd /opt/SVDB && pip install -e .

    conda config --add channels defaults
    conda config --add channels conda-forge
    conda config --add channels bioconda

    conda install -c bioconda samtools vt

    pip install genmod pyaml

