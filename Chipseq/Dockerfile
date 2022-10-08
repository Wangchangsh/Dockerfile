FROM snakemake/snakemake:latest

LABEL author="Wang Pengfei" \
      description="Chipseq pipeline Docker image"

RUN apt-get -y update \
    && apt-get install -y libcurl4-openssl-dev \
    && apt-get install -y samtools \
    && apt-get install -y bowtie2 \
    && apt-get install -y macs \
    && apt-get install -y default-jdk

RUN cd /opt \
    && wget --no-check-certificate https://kgithub.com/broadinstitute/picard/releases/download/2.27.4/picard.jar
 
RUN cd /usr/bin \
    && wget http://opengene.org/fastp/fastp \
    && chmod 777 ./fastp

RUN pip install deeptools
