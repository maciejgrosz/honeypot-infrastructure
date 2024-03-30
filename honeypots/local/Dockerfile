# Use Ubuntu as the base image
FROM --platform=linux/amd64 ubuntu:18.04

# Set non-interactive mode for apt-get
ENV DEBIAN_FRONTEND=noninteractive

# Install necessary build dependencies
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        git \
        build-essential \
        cmake \
        check \
        cython3 \
        libcurl4-openssl-dev \
        libemu-dev \
        libev-dev \
        libglib2.0-dev \
        libloudmouth1-dev \
        libnetfilter-queue-dev \
        libnl-3-dev \
        libpcap-dev \
        libssl-dev \
        libtool \
        libudns-dev \
        python3 \
        python3-dev \
        python3-bson \
        python3-yaml \
        python3-boto3 \
        fonts-liberation \
        vim && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Clone Dionea repository
RUN git clone --depth 1 --branch 0.10.0 https://github.com/DinoTools/dionaea.git /opt/dionaea

# Set working directory
WORKDIR /opt/dionaea

# Copy configuration files
COPY dionaea.cfg /opt/dionaea/etc/dionaea/dionaea.cfg
COPY ftp.yaml /opt/dionaea/etc/dionaea/services-enabled/
COPY ftp.py /opt/dionaea/modules/python/dionaea/ftp.py 

# Build Dionea
RUN mkdir build && \
    cd build && \
    cmake -DCMAKE_INSTALL_PREFIX:PATH=/opt/dionaea .. && \
    make && \
    make install

# Entry point
CMD ["/opt/dionaea/bin/dionaea"]
