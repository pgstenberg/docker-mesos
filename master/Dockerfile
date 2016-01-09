FROM pgstenberg/mesos-core

MAINTAINER Per-Gustaf Stenberg <per-gustaf.stenberg@stonepath.se>

ENV MESOS_PATH_VERSION=0.26.0

ENTRYPOINT /opt/mesos-${MESOS_PATH_VERSION}/build/bin/mesos-master.sh --ip=$(ip addr list eth0 |grep "inet " |cut -d' ' -f6|cut -d/ -f1) --work_dir=/var/lib/mesos
