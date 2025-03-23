FROM quay.io/centos/centos:stream10
ENV container=docker

RUN dnf install -y --refresh dnf-utils python3 python3-devel sudo https://dl.fedoraproject.org/pub/epel/epel-release-latest-10.noarch.rpm && \
    dnf config-manager --set-enabled crb && \
    dnf install -y epel-release && \
    dnf clean all

CMD ["/usr/sbin/init"]

VOLUME ["/sys/fs/cgroup", "/tmp", "/run"]
