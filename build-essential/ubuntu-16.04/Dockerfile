FROM ubuntu:16.04
MAINTAINER Esben Haabendal, eha@deif.com

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update -qq \
 && apt-get install -qq -y \
	build-essential ssh-client git subversion curl wget smbclient \
	check psmisc bc tofrodos \
	autoconf automake libtool gettext autoconf-archive pkg-config \
	doxygen \
	libjansson-dev \
	zlib1g-dev \
	ruby bundler \
	ssmtp \
	libnl-3-dev \
	libnl-cli-3-dev libnl-genl-3-dev libnl-nf-3-dev libnl-route-3-dev \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

# /bin/sh should be bash
RUN echo "dash dash/sh boolean false" | debconf-set-selections \
 && dpkg-reconfigure dash

# Install skalibs
RUN git clone git://github.com/skarnet/skalibs.git \
 && cd skalibs \
 && git checkout v2.3.10.0 \
 && ./configure \
 && make install \
 && cd .. \
 && rm -rf skalibs
