FROM node:15-stretch
LABEL maintainer="juusujanar"

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    ca-certificates \
    curl \
    openssl \
    unzip && \
    rm -rf /var/lib/apt/lists/*

ARG WATCHMAN_VERSION=v2021.02.01.00

RUN cd /tmp && \
    mkdir -p /usr/local/{bin,lib} /usr/local/var/run/watchman && \
    curl --silent --location --output watchman.zip "https://github.com/facebook/watchman/releases/download/${WATCHMAN_VERSION}/watchman-${WATCHMAN_VERSION}-linux.zip" && \
    unzip watchman.zip && \
    cp watchman-$WATCHMAN_VERSION-linux/bin/* /usr/local/bin && \
    cp watchman-$WATCHMAN_VERSION-linux/lib/* /usr/local/lib && \
    chmod 755 /usr/local/bin/watchman && \
    chmod 2777 /usr/local/var/run/watchman && \
    rm watchman.zip
    