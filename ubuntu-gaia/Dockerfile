FROM ubuntu:16.04
MAINTAINER jmp
# Install library dependencies
RUN apt-get update
RUN apt-get -y install git-core
RUN apt-get -y install build-essential     
RUN apt-get -y install libqt4-dev 
RUN apt-get -y install libyaml-dev
RUN apt-get install -y swig
# RUN cd swig
# RUN sudo apt-get install automake
# RUN ./autogen.sh
# RUN ./configure
# RUN sudo apt-get -y install bison flex
# RUN make
# RUN sudo make install
RUN apt-get -y install python-dev
RUN apt-get -y install pkg-config
RUN apt-get -y install libeigen3-dev

# gaia installation
RUN ./waf configure --download --with-python-bindings
RUN ./waf install

# final command
RUN echo "hello gaia-Pantelis"