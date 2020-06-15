FROM ubuntu:18.04
MAINTAINER jmp
# Install library dependencies
RUN apt-get update
RUN apt-get -y install git-core
RUN apt-get -y install build-essential     
RUN apt-get -y install libqt4-dev 
RUN apt-get -y install libyaml-dev
RUN apt-get install -y swig
RUN apt-get -y install python-dev
RUN apt-get -y install pkg-config
RUN apt-get -y install libeigen3-dev

ADD gaia /gaia/
ADD acousticbrainz-datasets /acousticbrainz-datasets/

# gaia installation
# RUN cd gaia
RUN chmod +x gaia/waf
RUN gaia/./waf configure --download --with-python-bindings
RUN gaia/./waf
RUN gaia/./waf install

# final command
RUN echo "hello gaia-Pantelis"