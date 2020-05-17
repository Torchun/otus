FROM nvidia/cuda:latest

ENV DEBIAN_FRONTEND noninteractive
ENV TERM linux

RUN mkdir /data

RUN set -ex \
    && apt-get update -yqq \
    && apt-get upgrade -yqq \
    && apt-get install -yqq --no-install-recommends \
        git \
        wget \
        curl \
        ssh \
        libxrender1 \
        libxext6 \
        software-properties-common \
        apt-utils \
        net-tools \
        iproute2 \
        screen \
        nmon \
        htop \
        vim \
    && wget --no-check-certificate https://repo.continuum.io/miniconda/Miniconda3-4.7.12.1-Linux-x86_64.sh \
    && /bin/bash Miniconda3-4.7.12.1-Linux-x86_64.sh -f -b -p /opt/miniconda \
    && /opt/miniconda/bin/conda install conda=4.8.1 \
    && /opt/miniconda/bin/conda install python=3.6 \
    && /opt/miniconda/bin/conda clean -yq -a \
    && rm Miniconda3-4.7.12.1-Linux-x86_64.sh \
    && rm -rf \
        /tmp/* \
        /var/tmp/* \
        /usr/share/man \
        /usr/share/doc \
        /usr/share/doc-base

ENV PATH /opt/miniconda/bin:$PATH

# default ML packets
RUN conda install -y \
    pandas \
    numpy \
    cloudpickle \
    dill \
    flask \
    psycopg2 \
    pyaudio \
    ipython \
    scikit-learn \
    seaborn \
    matplotlib \
    scipy \
    pydot \
    graphviz \
    tqdm \ 
    ipython \
    ipywidgets \
  && conda install -c conda-forge -y \
    imbalanced-learn \
    category_encoders \
  && conda install -c conda-forge -y jupyterlab \
    librosa \
  && pip install pyAudioAnalysis \
  && conda install conda

# ML on GPU: https://rapids.ai/start.html#rapids-release-selector
RUN conda install -c rapidsai -c nvidia -c conda-forge -c defaults -y \
    rapids=0.13 \
    cudatoolkit=10.2

# DL packets
RUN conda install -c pytorch -y \
    pytorch \
    torchvision
RUN pip install --upgrade tensorflow

# verify installation
RUN python -c "import tensorflow as tf;print(tf.reduce_sum(tf.random.normal([1000, 1000])))"

WORKDIR /data

CMD [ "/bin/bash" ]
