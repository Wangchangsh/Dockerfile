FROM ubuntu

LABEL author="Wang Pengfei" \
      description="Python3 Docker image"

RUN apt-get -y update \
    && apt-get install -y build-essential \
    && apt-get install -y zlib1g-dev \
    && apt-get install -y libncurses5-dev \
    && apt-get install -y libgdbm-dev \
    && apt-get install -y libnss3-dev \
    && apt-get install -y libssl-dev \
    && apt-get install -y libreadline-dev \
    && apt-get install -y wget \
    && apt-get install -y libffi-dev \
    && apt-get install -y libsqlite3-dev \
    && apt-get install -y libbz2-dev \
    && apt-get install -y liblzma-dev \
    && apt-get install -y lzma \
    && rm -rf /var/lib/apt/lists/*

RUN wget https://www.python.org/ftp/python/3.7.14/Python-3.7.14.tgz \
    && tar -zxvf Python-3.7.14.tgz \
    && cd Python-3.7.14 \
    && ./configure --prefix=/opt/python3 --enable-optimizations \
    && make \
    && make altinstall \
    && cd .. \
    && rm -rf Python-3.7.14*

ENV PATH=/opt/python3/bin:$PATH

RUN ln -sf /opt/python3/bin/python3.7 /usr/bin/python3
RUN ln -sf /opt/python3/bin/python3.7 /usr/bin/python

RUN pip3.7 install numpy
RUN pip3.7 install Biopython
RUN pip3.7 install matplotlib
RUN pip3.7 install jcvi