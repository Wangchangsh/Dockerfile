FROM changshengw6/python:3.8

LABEL author="Wang Pengfei" \
      description="Genome alignment Docker image"

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get -y update \
    && apt install -y perl \
    && apt install -y gawk \
    && apt install -y sed \
    && apt install -y git \
    && apt install -y curl \
    && rm -rf /var/lib/apt/lists/*

RUN pip3 install numpy==1.21.2
RUN pip3 install scipy==1.6.2
RUN pip3 install python-igraph==0.9.1
RUN pip3 install psutil==5.8.0
RUN pip3 install pysam==0.16.0.1
RUN pip3 install matplotlib==3.3.4
RUN pip3 install setuptools
RUN pip3 install Cython==0.29.23 --install-option="--no-cython-compile"

RUN cd /opt \ 
    && git clone https://kgithub.com/schneebergerlab/syri.git \
    && cd syri \
    && python3 setup.py install

RUN cd /opt \ 
    && git clone https://kgithub.com/schneebergerlab/plotsr.git \
    && cd plotsr \
    && python3 setup.py install

RUN wget https://kgithub.com/mummer4/mummer/releases/download/v4.0.0rc1/mummer-4.0.0rc1.tar.gz \
    && tar -zxvf mummer-4.0.0rc1.tar.gz \
    && cd mummer-4.0.0rc1 \
    && ./configure --prefix=/opt/mummer4 \
    && make \
    && make install \
    && cd .. \
    && rm -rf mummer-4.0.0rc1*

RUN chmod 777 /opt/syri/bin/syri \
    && chmod 777 /opt/syri/bin/chroder

ENV PATH=/opt/mummer4/bin:$PATH
ENV PATH=/opt/syri/bin:$PATH
ENV PATH=/opt/plotsr/bin:$PATH