FROM ubuntu

LABEL author="Wang Pengfei" \
      description="Poplation genetics Docker image"

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get -y update \
    && apt-get install -y make \
    && apt-get install -y wget \
    && apt-get install -y gcc \
    && apt-get install -y libgsl-dev \
    && apt-get install -y liblapacke-dev \
    && apt-get install -y liblapack-dev \
    && apt-get install -y libopenblas-dev \
    && rm -rf /var/lib/apt/lists/*

RUN cd opt \
    && wget https://github.com/DReichLab/EIG/archive/refs/tags/v8.0.0.tar.gz \
    && tar -zxvf v8.0.0.tar.gz \
    && rm v8.0.0.tar.gz \
    && cd EIG-8.0.0/src \
    && make LDLIBS="-llapacke"\
    && make install

ENV PATH=/opt/EIG-8.0.0/bin:$PATH