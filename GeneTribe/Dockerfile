FROM changshengw6/python:3.7

LABEL author="Wang Pengfei" \
      description="GeneTribe Docker image"

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get -y update \
    && apt-get install -y bedtools \
    && apt-get install -y git \
    && apt-get install -y gawk \
    && apt-get install -y liblzma-dev \
    && apt-get install -y lzma \
    && apt-get install -y texlive \
    && apt-get install -y texlive-latex-recommended \
    && apt-get install -y texlive-latex-extra \
    && rm -rf /var/lib/apt/lists/*

RUN wget --output-document blast.tar.gz https://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/ncbi-blast-2.13.0+-x64-linux.tar.gz \
    && tar -zxvf blast.tar.gz -C /opt \
    && rm -f blast.tar.gz

ENV PATH=/opt/ncbi-blast-2.13.0+/bin:$PATH

RUN ln -sf /opt/python3/bin/python3.7 /usr/bin/python3
RUN ln -sf /opt/python3/bin/python3.7 /usr/bin/python

RUN pip3.7 install latex

RUN cd /opt \
    && git clone https://kgithub.com/chenym1/genetribe.git \
    && cd genetribe \
    && ./install.sh

ENV PATH=/opt/genetribe:$PATH