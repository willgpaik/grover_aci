Bootstrap: docker
From: nvidia/cuda:10.0-cudnn7-devel-ubuntu16.04

%environment
    export LC_ALL=C.UTF-8
    export LANG=C.UTF-8
    export PATH=/opt/conda/bin:/usr/local/nvidia/bin/:$PATH
    export LD_LIBRARY_PATH=/usr/local/nvidia/lib:/usr/local/nvidia/lib64
    export NVIDIA_VISIBLE_DEVICES=all
    export NVIDIA_DRIVER_CAPABILITIES=compute,utility
    export PYTHONPATH=/grover

%post
    apt-get update && apt-get install -y --no-install-recommends \
            build-essential \
            cmake \
            git \
            curl \
            vim \
            ca-certificates \
            libjpeg-dev \
            libpng-dev \
            wget &&\
            rm -rf /var/lib/apt/lists/*

    curl -o ~/miniconda.sh -O  https://repo.continuum.io/miniconda/Miniconda3-4.5.4-Linux-x86_64.sh  && \
    chmod +x ~/miniconda.sh && \
    ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh && \
    /opt/conda/bin/conda install -y python=3.6 tqdm numpy pyyaml scipy ipython mkl mkl-include cython typing h5py pandas && \
    /opt/conda/bin/conda clean -ya && /opt/conda/bin/pip install tensorflow-gpu==1.13.1

    export LC_ALL=C.UTF-8
    export LANG=C.UTF-8
    export PATH=/opt/conda/bin:/usr/local/nvidia/bin/:$PATH
    export LD_LIBRARY_PATH=/usr/local/nvidia/lib:/usr/local/nvidia/lib64
    export NVIDIA_VISIBLE_DEVICES=all
    export NVIDIA_DRIVER_CAPABILITIES=compute,utility
    
    mkdir -p grover
    cd /grover

    wget https://raw.githubusercontent.com/rowanz/grover/master/requirements-gpu.txt
    pip install -r requirements-gpu.txt

    export PYTHONPATH=/grover
