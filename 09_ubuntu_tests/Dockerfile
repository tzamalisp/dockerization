FROM ubuntu:18.04
MAINTAINER jmp

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    ipython3 \
    python3-pip \
    python3-dev \
    python3-numpy-dev \
   	python3-numpy

RUN ln -sf /usr/bin/python3 /usr/bin/python
RUN ln -sf /usr/bin/pip3 /usr/bin/pip

# CMD ["python"]
