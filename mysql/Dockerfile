# -----------------------------------------------------
# MySQL Server + Client Image
#
# Ubuntu base with the Oracle MySQL APT repository and a
# full MySQL server install. Runnable as a Pterodactyl
# installation image, a standalone database, or as the
# base for the MySQL runtime yolks.
# -----------------------------------------------------
ARG MYSQL_VERSION=8.4
FROM        --platform=$TARGETOS/$TARGETARCH ubuntu:24.04

ARG MYSQL_VERSION

LABEL       author="NotYusta" maintainer="xabhista19@gmail.com"

LABEL       org.opencontainers.image.source="https://github.com/NotYusta/image-yolks"
LABEL       org.opencontainers.image.licenses=MIT

ENV         DEBIAN_FRONTEND=noninteractive

RUN         apt-get update \
            && apt-get -y --no-install-recommends install \
                ca-certificates \
                curl \
                git \
                gnupg \
                iproute2 \
                jq \
                netcat-traditional \
                tar \
                unzip \
                wget \
                zip \
            && install -d /usr/share/keyrings \
            && export GNUPGHOME="$(mktemp -d)" \
            && gpg --batch --keyserver keyserver.ubuntu.com --recv-keys 'BCA43417C3B485DD128EC6D4B7B3B788A8D3785C' \
            && gpg --batch --export 'BCA43417C3B485DD128EC6D4B7B3B788A8D3785C' > /usr/share/keyrings/mysql.gpg \
            && rm -rf "$GNUPGHOME" \
            && echo "deb [signed-by=/usr/share/keyrings/mysql.gpg] http://repo.mysql.com/apt/ubuntu/ noble mysql-${MYSQL_VERSION}-lts" > /etc/apt/sources.list.d/mysql.list \
            && printf '#!/bin/sh\nexit 101\n' > /usr/sbin/policy-rc.d \
            && chmod +x /usr/sbin/policy-rc.d \
            && apt-get update \
            && apt-get -y install mysql-community-server \
            && rm -f /usr/sbin/policy-rc.d \
            && apt-get clean \
            && rm -rf /var/lib/apt/lists/*
