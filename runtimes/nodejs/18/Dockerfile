FROM --platform=$TARGETOS/$TARGETARCH node:18-bullseye-slim

LABEL       author="Jesper Richert" maintainer="hey@jespersen.zip"

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        ffmpeg \
        iproute2 \
        git \
        libsqlite3-dev \
        python3 \
        python3-dev \
        ca-certificates \
        dnsutils \
        tzdata \
        zip \
        tar \
        curl \
        build-essential \
        libtool && \
    npm install -g npm@latest && \
    rm -rf /var/lib/apt/lists/*

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
