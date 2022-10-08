FROM snakemake/snakemake:latest

LABEL author="Wang Pengfei" \
      description="RNAseq pipeline Docker image"

RUN apt-get -y update \
    && apt-get install -y subread \
    && apt-get install -y hisat2 \
    && apt-get install -y samtools

RUN cd /usr/bin \
    && wget http://opengene.org/fastp/fastp \
    && chmod 777 ./fastp