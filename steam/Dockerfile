FROM alpine
MAINTAINER Cedric Dumay <cedric.dumay@gmail.com>

RUN apk --update add bash curl
ENV INSTALL_DIR="/opt/steam"

# we setup base dir
RUN mkdir -p "${INSTALL_DIR}" && \
    adduser -S -h "${INSTALL_DIR}" -g "" -s "/bin/bash" -u 1000 steam && \
    echo "steam ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers && \
    chown -R steam: "${INSTALL_DIR}"

# we install steamcmd
WORKDIR "${INSTALL_DIR}"
RUN curl -Ss "https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz" | tar xzv && \
    chmod +x "${INSTALL_DIR}/steamcmd.sh"
