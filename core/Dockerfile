FROM ubuntu:14.04

MAINTAINER Per-Gustaf Stenberg <per-gustaf.stenberg@stonepath.se>

ENV MESOS_PATH_VERSION=0.26.0

# Install JAVA8
RUN apt-get install -y software-properties-common && add-apt-repository -y ppa:webupd8team/java && apt-get update
RUN echo "oracle-java8-installer shared/accepted-oracle-license-v1-1 select true" | sudo debconf-set-selections
RUN apt-get install -y oracle-java8-installer

# Install dependencies
RUN apt-get update && apt-get install -y build-essential libtool zlib1g-dev python-dev python-boto libcurl4-nss-dev libsasl2-dev libsasl2-modules libapr1-dev libsvn-dev
RUN apt-get -y --no-install-recommends install maven

# Download mesos source
ADD http://www.apache.org/dist/mesos/$MESOS_PATH_VERSION/mesos-$MESOS_PATH_VERSION.tar.gz /opt/mesos-$MESOS_PATH_VERSION.tar.gz
RUN tar -zxf /opt/mesos-$MESOS_PATH_VERSION.tar.gz -C /opt
WORKDIR /opt/mesos-$MESOS_PATH_VERSION

# Compile mesos
RUN mkdir build
WORKDIR /opt/mesos-$MESOS_PATH_VERSION/build
RUN ../configure
RUN make -j $(cat /proc/cpuinfo | grep processor | wc -l) V=0
WORKDIR /opt/mesos-$MESOS_PATH_VERSION/build/bin
