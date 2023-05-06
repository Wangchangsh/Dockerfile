FROM broadinstitute/gatk:4.3.0.0

LABEL author="Wang Pengfei" \
      description="SNPCalling pipeline Docker image"

ENV DEBIAN_FRONTEND=noninteractive

RUN conda install -y -c bioconda fastp
RUN conda install -y -c bioconda samtools
RUN conda install -y -c bioconda bwa