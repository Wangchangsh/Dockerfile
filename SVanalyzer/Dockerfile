FROM ubuntu:20.04

ENV DEBIAN_FRONTEND=noninteractive

ARG svanalyzer=0.36

LABEL base.image="ubuntu:20.04"
LABEL software="svanalyszer"
LABEL software.version=$EDTA
LABEL description="SVanalyzer is a software package for the analysis of large insertions, deletions, and inversions in DNA"
LABEL website="https://github.com/nhansen/SVanalyzer"
LABEL maintainer="Changsheng Wang"
LABEL maintainer.email="changshengw6@gmail.com"

RUN apt-get -y update \
    && apt install -y perl \
    && apt install -y git \
    && apt install -y wget \
    && apt install -y build-essential \
    && apt install -y libmodule-build-perl \
    && apt install -y liblog-log4perl-perl \
    && apt install -y samtools \
    && apt install -y bedtools \
    && apt install -y edlib-aligner \
    && rm -rf /var/lib/apt/lists/*

RUN wget https://github.com/mummer4/mummer/releases/download/v4.0.0rc1/mummer-4.0.0rc1.tar.gz \
    && tar -zxvf mummer-4.0.0rc1.tar.gz \
    && cd mummer-4.0.0rc1 \
    && ./configure --prefix=/opt/mummer4 \
    && make \
    && make install \
    && cd .. \
    && rm -rf mummer-4.0.0rc1*

ENV PATH /opt/mummer4/bin:$PATH

RUN cd /opt \
    && git clone https://github.com/nhansen/SVanalyzer.git \
    && cd SVanalyzer \
    && perl Build.PL \
    && ./Build \
    && ./Build install

ENV PATH /opt/SVanalyzer/scripts:${PATH}
ENV PATH /opt/SVanalyzer/scripts/misc:${PATH}