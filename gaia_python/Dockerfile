FROM metabrainz/python:2.7 AS gaiajmp

# Dockerize
ENV DOCKERIZE_VERSION v0.6.1
RUN wget https://github.com/jwilder/dockerize/releases/download/$DOCKERIZE_VERSION/dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && tar -C /usr/local/bin -xzvf dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz

# Install dependencies
# Hadolint DL4006
SHELL ["/bin/bash", "-o", "pipefail", "-c"]
# Node
RUN wget -q -O - https://deb.nodesource.com/setup_12.x | bash - && apt-get update \
    && apt-get install -y --no-install-recommends \
                       build-essential \
                       ca-certificates \
                       git \
                       ipython \
                       libavcodec-dev \
                       libavformat-dev \
                       libavutil-dev \
                       libavresample-dev \
                       libffi-dev \
                       libfftw3-dev \
                       libpq-dev \
                       libsamplerate0-dev \
                       libqt4-dev \
                       libssl-dev \
                       libtag1-dev \
                       libxml2-dev \
                       libxslt1-dev \
                       libyaml-dev \
                       pkg-config \
                       pxz \
                       python-dev \
                       python-numpy-dev \
                       python-numpy \
                       swig2.0 \
    && rm -rf /var/lib/apt/lists/*

# RUN mkdir /code
# RUN mkdir /data
# WORKDIR /code

# Gaia
# See https://github.com/MTG/gaia
RUN git clone https://github.com/MTG/gaia /tmp/gaia \
    && cd /tmp/gaia \
    && git checkout v2.4.5 \
    && ./waf configure --with-python-bindings \
    && ./waf \
    && ./waf install \
    && cd / && rm -r /tmp/gaia

# Python dependencies
COPY requirements.txt requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

COPY requirements_development.txt requirements_development.txt
RUN pip install --no-cache-dir -r requirements_development.txt

CMD ["python", "-m", "gaia2.scripts.classification.train_model_from_sigs"]
