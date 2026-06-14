FROM        --platform=$TARGETOS/$TARGETARCH debian:latest

LABEL       author="Jesper Richert" maintainer="hey@jespersen.zip"

ENV         DEBIAN_FRONTEND noninteractive

RUN         apt update -y \
    && apt upgrade -y \
    && apt install -y apt-transport-https wget curl iproute2 libgdiplus tini \
    && wget https://dot.net/v1/dotnet-install.sh \
    && chmod +x dotnet-install.sh \
    && DOTNET_VERSION=$(curl -sSL https://dotnet.microsoft.com/en-us/download/dotnet/9.0 | grep -oP 'SDK 9\.\d+\.\d+' | head -1 | awk '{print $2}') \
    && ./dotnet-install.sh -i /usr/share -v "$DOTNET_VERSION" --channel 9.0.0-preview \
    && ln -s /usr/share/dotnet/dotnet /usr/bin/dotnet


USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

STOPSIGNAL SIGINT


COPY        ../entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]