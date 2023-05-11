FROM rocker/tidyverse:4.1.3

ENV DEBIAN_FRONTEND noninteractive

ARG mpMap2=1.0.4

LABEL base.image="rocker/tidyverse:4.1.3"
LABEL version=${mpMap2}
LABEL description="Map construction for multi-parent crosses"
LABEL website="https://github.com/rohan-shah/mpMap2"
LABEL maintainer="Changsheng Wang"
LABEL maintainer.email="changshengw6@gmail.com"

RUN install2.r --error --skipinstalled \
    --repos 'https://mirrors.tuna.tsinghua.edu.cn/CRAN/' \
    vcfR optparse sn fastcluster nnls qtl pryr igraph

RUN install2.r --error \
    -r http://bioconductor.org/packages/3.17/bioc \
    Heatplus \
    && rm -rf /tmp/downloaded_packages/

RUN install2.r --error car

RUN wget -c https://cran.r-project.org/src/contrib/Archive/mpMap2/mpMap2_${mpMap2}.tar.gz \
    && R CMD INSTALL mpMap2_${mpMap2}.tar.gz \
    && rm mpMap2_${mpMap2}.tar.gz