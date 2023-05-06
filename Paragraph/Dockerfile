FROM ubuntu:18.04

LABEL author="Wang Pengfei" \
      description="Paragraph Docker image"

ENV DEBIAN_FRONTEND=noninteractive

RUN printf "Acquire::http::Pipeline-Depth 0;\nAcquire::http::No-Cache true;\nAcquire::BrokenProxy true;" > /etc/apt/apt.conf.d/99fixbadproxy

RUN apt-get -y update \
    && apt-get install -y autoconf \
    && apt-get install -y automake \
    && apt-get install -y build-essential \
    && apt-get install -y cmake \
    && apt-get install -y libboost-all-dev \
    && apt-get install -y libfreetype6-dev \
    && apt-get install -y libpng-dev \
    && apt-get install -y liblzma-dev \
    && apt-get install -y libtool \
    && apt-get install -y python3-pip \
    && apt-get install -y python-pkgconfig \
    && apt-get install -y m4 \
    && apt-get install -y software-properties-common \
    && apt-get install -y zlib1g-dev \
    && apt-get install -y libbz2-dev \
    && apt-get install -y git \
    && rm -rf /var/lib/apt/lists/*


RUN pip3 install nose
RUN pip3 install mock
RUN pip3 install intervaltree
RUN pip3 install pysam
RUN pip3 install jsonschema
RUN pip3 install pylint
RUN pip3 install pep8

RUN git clone https://kgithub.com/Wangchangsh/paragraph.git \
    && cd paragraph \
    && cmake . -DCMAKE_INSTALL_PREFIX=/opt/paragraph \
    && make \
    && make install \
    && cd .. \
    && rm -rf paragraph

ENTRYPOINT ["/usr/bin/python3"]
CMD ["/opt/paragraph/bin/multigrmpy.py", "-h"]