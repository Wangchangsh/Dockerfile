FROM ubuntu:20.04

LABEL author="Wang Pengfei" \
      description="Pangenie Docker image"

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get -y update \
    && apt-get install -y software-properties-common \
    && apt-get install -y build-essential \
    && apt-get install -y cmake \
    && apt-get install -y git \
    && apt-get install -y zlib1g-dev \
    && apt-get install -y libjellyfish-2.0-dev \
    && apt-get install -y pkg-config \
    && rm -rf /var/lib/apt/lists/*

RUN mkdir /metadata \
    && echo `dpkg -l | grep jellyfish | tr -s " " | cut -d " " -f 2,3` > /metadata/jellyfish.lib.version

RUN cd /opt \
    && git clone https://github.com/eblerjana/pangenie.git \
    && cd pangenie \
    && mkdir build \
    && cd build \
    && cmake .. \
    && make -j 4 \
    && cp src/PanGenie /usr/local/bin \
    && cp src/PanGenie-graph /usr/local/bin

RUN echo `git rev-parse --short HEAD` > /metadata/pangenie.git.version