FROM ubuntu

LABEL author="Wang Pengfei" \
      description="Python2 Docker image"

RUN apt-get -y update \
    && apt-get install -y python2 \
    && apt-get install -y curl

RUN curl https://bootstrap.pypa.io/pip/2.7/get-pip.py --output get-pip.py \
    && python2 get-pip.py

RUN pip2 install numpy
RUN pip2 install matplotlib

