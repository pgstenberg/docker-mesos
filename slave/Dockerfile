FROM pgstenberg/mesos-core

MAINTAINER Per-Gustaf Stenberg <per-gustaf.stenberg@stonepath.se>

ENV MESOS_PATH_VERSION=0.26.0
ENV MESOS_MASTER_PORT 5050

ENTRYPOINT /opt/mesos-${MESOS_PATH_VERSION}/build/bin/mesos-slave.sh --master=${MESOS_MASTER}:${MESOS_MASTER_PORT}
