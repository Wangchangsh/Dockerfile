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

RUN cd /opt \
    && wget https://github.com/gpertea/stringtie/releases/download/v2.2.1/stringtie-2.2.1.Linux_x86_64.tar.gz \
    && tar -zxvf stringtie-2.2.1.Linux_x86_64.tar.gz \
    && rm stringtie-2.2.1.Linux_x86_64.tar.gz

ENV PATH=/opt/stringtie-2.2.1.Linux_x86_64:$PATH