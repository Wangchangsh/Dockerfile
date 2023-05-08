FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

ARG isoseq3=3.8.2
ARG lima=2.6.0
ARG pbaa=1.0.3
ARG pbccs=6.4.0
ARG pbfusion=0.1.0
ARG pbmarkdup=1.0.3
ARG pbmm2=1.10.0
ARG pbpigeon=1.0.0
ARG pbskera=0.1.0
ARG pbsv=2.9.0
ARG pbtk=3.1.0
ARG recalladapters=9.0.0
ARG trgt=0.4.0

LABEL base.image="ubuntu:22.04"
LABEL description="PacBio® tools distributed"
LABEL website="https://github.com/PacificBiosciences/pbbioconda"
LABEL maintainer="Changsheng Wang"
LABEL maintainer.email="changshengw6@gmail.com"

RUN apt-get -y update \
    && apt-get install -y wget \
    && rm -rf /var/lib/apt/lists/*

RUN wget https://mirrors.tuna.tsinghua.edu.cn/anaconda/miniconda/Miniconda2-py27_4.8.3-Linux-x86_64.sh \
    && sh Miniconda2-py27_4.8.3-Linux-x86_64.sh -b -p /opt/miniconda2 \
    && rm -rf Miniconda2-py27_4.8.3-Linux-x86_64.sh

ENV PATH /opt/miniconda2/bin:$PATH

RUN conda config --add channels bioconda

RUN conda install -c bioconda -y isoseq3=${isoseq3}
RUN conda install -c bioconda -y lima=${lima}
RUN conda install -c bioconda -y pbaa=${pbaa}
RUN conda install -c bioconda -y pbccs=${pbccs}
RUN conda install -c bioconda -y pbfusion=${pbfusion}
RUN conda install -c bioconda -y pbmarkdup=${pbmarkdup}
RUN conda install -c bioconda -y pbmm2=${pbmm2}
RUN conda install -c bioconda -y pbpigeon=${pbpigeon}
RUN conda install -c bioconda -y pbskera=${pbskera}
RUN conda install -c bioconda -y pbsv=${pbsv}
RUN conda install -c bioconda -y pbtk=${pbtk}
RUN conda install -c bioconda -y recalladapters=${recalladapters}
RUN conda install -c bioconda -y trgt=${trgt}
RUN conda clean --all -f -y