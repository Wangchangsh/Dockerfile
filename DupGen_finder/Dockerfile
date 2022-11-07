FROM ubuntu

LABEL author="Wang Pengfei" \
      description="duplicated gene finder pipeline Docker image"

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get -y update \
    && apt install -y perl \
    && apt install -y git \
    && apt install -y make \
    && apt install -y build-essential \
    && rm -rf /var/lib/apt/lists/*

RUN cd /opt \
    && git clone https://github.com/qiao-xin/DupGen_finder.git \
    && cd DupGen_finder \
    && make \
    && chmod 775 DupGen_finder.pl \
    && chmod 775 DupGen_finder-unique.pl

ENV PATH=/opt/DupGen_finder:$PATH