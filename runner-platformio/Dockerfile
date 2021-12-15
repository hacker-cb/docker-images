FROM ubuntu:latest
LABEL maintainer="Pavel Sokolov <pavel@sokolov.me>"

RUN export DEBIAN_FRONTEND=noninteractive \
    && \
    apt update -qq \
    && \
    apt install -y \
      build-essential \
      python3-pip \
      python3-protobuf \
      protobuf-compiler \
      cmake \
    && \
    pip3 install -U platformio \
    && echo "DONE" \