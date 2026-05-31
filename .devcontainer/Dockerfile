FROM debian:bookworm

ARG PGVERSION=16

RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates gnupg postgresql-common \
    && /usr/share/postgresql-common/pgdg/apt.postgresql.org.sh -y \
    && apt-get update \
    && apt-get install -y --no-install-recommends \
    autoconf \
    automake \
    build-essential \
    git \
    libc-ares-dev \
    libevent-dev \
    libldap-dev \
    libpam0g-dev \
    libssl-dev \
    ldap-utils \
    libtool \
    pandoc \
    pkg-config \
    postgresql-${PGVERSION} \
    python3 \
    python3-pip \
    python3-venv \
    slapd \
    socat \
    sudo \
    && rm -rf /var/lib/apt/lists/*

RUN useradd -m -s /bin/bash dev \
    && echo 'dev ALL=(ALL) NOPASSWD: ALL' >> /etc/sudoers

USER dev
WORKDIR /home/dev

RUN python3 -m venv /home/dev/venv
ENV PATH="/home/dev/venv/bin:/usr/lib/postgresql/${PGVERSION}/bin:${PATH}"
