FROM ubuntu:20.04
ENV DEBIAN_FRONTEND=noninteractive
RUN sed -i 's@//.*archive.ubuntu.com@//mirrors.ustc.edu.cn@g' /etc/apt/sources.list
RUN apt-get update -qq && \
    apt-get install -y curl git build-essential chrpath gcc-multilib ninja-build cmake && \
    apt-get clean
RUN apt-get update -qq && \
    apt-get install -y file pkg-config python3 libxml2-dev zlib1g-dev libzstd-dev && \
    apt-get clean
RUN apt-get update -qq && \
    apt-get install -y curl && \
    apt-get clean
RUN ALL_PROXY=http://192.168.122.1:1083 \
    curl -L https://github.com/Kitware/CMake/releases/download/v3.28.5/cmake-3.28.5-linux-x86_64.tar.gz | \
    tar -C /usr --strip-components=1 --gzip -xvf -
RUN cmake --version

