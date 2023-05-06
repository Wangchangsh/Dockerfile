FROM continuumio/miniconda3:4.3.27

ENV DEBIAN_FRONTEND=noninteractive

ARG EDTA=2.1.0

LABEL base.image="continuumio/miniconda3:4.3.27"
LABEL software="EDTA"
LABEL software.version=$EDTA
LABEL description="EDTA: an Extensive de-novo TE Annotator for eukaryotic genomes"
LABEL website="https://github.com/oushujun/EDTA"
LABEL maintainer="Changsheng Wang"
LABEL maintainer.email="changshengw6@gmail.com"

RUN conda config --add channels defaults
RUN conda config --add channels bioconda
RUN conda config --add channels conda-forge

RUN conda install -c conda-forge mamba \
    && conda clean --all -f --yes

RUN mamba install -c conda-forge -y tensorflow=1.14
RUN mamba install -c bioconda -y edta=2.1.0 \
    && mamba clean --all -f --yes

ENV PATH /opt/conda/share/EDTA/:$PATH