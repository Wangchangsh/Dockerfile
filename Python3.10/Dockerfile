FROM ubuntu

LABEL author="Wang Pengfei" \
      description="Python3.10 Docker image"

ENV DEBIAN_FRONTEND=noninteractive

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

RUN wget https://www.python.org/ftp/python/3.10.8/Python-3.10.8.tgz \
    && tar -zxvf Python-3.10.8.tgz \
    && cd Python-3.10.8 \
    && ./configure --prefix=/opt/python3 --enable-optimizations \
    && make \
    && make altinstall \
    && cd .. \
    && rm -rf Python-3.10.8*

ENV PATH=/opt/python3/bin:$PATH

RUN ln -sf /opt/python3/bin/python3.10 /usr/bin/python3
RUN ln -sf /opt/python3/bin/python3.10 /usr/bin/python
RUN ln -sf /opt/python3/bin/pip3.10 /usr/bin/pip3