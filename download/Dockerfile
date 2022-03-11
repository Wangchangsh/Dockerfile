FROM ubuntu

LABEL author="Wang Pengfei" \
      description="Docker image containing all software requirements for download released sequencing data"

RUN apt-get update \
    && apt-get install -y wget \
    && rm -rf /var/lib/apt/lists/*

RUN wget --output-document sratoolkit.tar.gz http://ftp-trace.ncbi.nlm.nih.gov/sra/sdk/current/sratoolkit.current-ubuntu64.tar.gz \
    && tar -zxvf sratoolkit.tar.gz -C /opt \
    && rm -f sratoolkit.tar.gz

ENV PATH=/opt/sratoolkit.2.11.2-ubuntu64/bin:$PATH

RUN wget https://d3gcli72yxqn2z.cloudfront.net/connect_latest/v4/bin/ibm-aspera-connect_4.1.1.73_linux.tar.gz \
    && tar -zxvf ibm-aspera-connect_4.1.1.73_linux.tar.gz \
    && bash ibm-aspera-connect_4.1.1.73_linux.sh \
    && mv ~/.aspera /opt/aspera \
    && rm -f ibm* \
    && cp /opt/aspera/connect/etc/asperaweb_id_dsa.* /usr

ENV PATH=/opt/aspera/connect/bin:$PATH