FROM rocker/tidyverse:4.2.2

LABEL author="Wang Pengfei" \
      description="R Docker image"

RUN install2.r --error --skipinstalled \
    --repos 'https://mirrors.tuna.tsinghua.edu.cn/CRAN/' \
    vcfR optparse gap corrr