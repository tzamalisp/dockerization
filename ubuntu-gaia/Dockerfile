FROM ubuntu:18.04

ENV LANG C.UTF-8
MAINTAINER jmp

RUN apt-get update \
    && apt-get -y upgrade \
    && apt-get install -y build-essential libqt4-dev libyaml-dev swig python-dev pkg-config libeigen3-dev git \
    && apt-get install -y python3-pip python3-dev \
    && cd /usr/local/bin \ 
    && ln -s /usr/bin/python3 python \
    && pip3 install --upgrade pip \
    && pip3 install PyYAML

ADD gaia /gaia/
ADD acousticbrainz-datasets /acousticbrainz-datasets/

RUN cd gaia \
    && python waf configure --with-python-bindings \
    && python waf \ 
    && python waf install \
    && cd 

CMD ["python", "-m", "gaia2.scripts.classification.train_model", "--help"]

# WORKDIR /gaiasample