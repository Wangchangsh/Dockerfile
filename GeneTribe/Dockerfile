FROM ubuntu

LABEL author="Wang Pengfei" \
      description="GeneTribe Docker image"

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get -y update \
    && apt-get install -y git \
    && apt-get install -y wget \
    && apt-get install -y gawk \
    && apt-get install -y build-essential \
    && apt-get install -y texlive \
    && apt-get install -y texlive-latex-recommended \
    && apt-get install -y texlive-latex-extra \
    && apt-get install -y texlive-fonts-recommended \
    && apt-get install -y dvipng \
    && apt-get install -y cm-super \
    && rm -rf /var/lib/apt/lists/*

RUN wget https://mirrors.tuna.tsinghua.edu.cn/anaconda/miniconda/Miniconda3-py37_4.12.0-Linux-x86_64.sh \
    && sh Miniconda3-py37_4.12.0-Linux-x86_64.sh -b -p /opt/miniconda3 \
    && rm -rf Miniconda3-py37_4.12.0-Linux-x86_64.sh

ENV PATH=/opt/miniconda3/bin:$PATH

RUN conda install -y blast==2.9.0 -c bioconda
RUN conda install -y bedtools==2.29.2 -c bioconda
RUN pip install jcvi==1.0.6
RUN pip3 install latex

RUN cd /opt \
    && git clone https://kgithub.com/chenym1/genetribe.git \
    && cd genetribe \
    && ./install.sh

ENV PATH=/opt/genetribe:$PATH