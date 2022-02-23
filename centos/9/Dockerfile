FROM quay.io/centos/centos:stream9
ENV container docker

RUN dnf install -y --refresh dnf-utils python3 sudo https://dl.fedoraproject.org/pub/epel/epel-release-latest-9.noarch.rpm && \
    dnf config-manager --set-enabled crb && \
    dnf install -y epel-next-release && \
    dnf clean all

CMD ["/usr/sbin/init"]

VOLUME ["/sys/fs/cgroup", "/tmp", "/run"]
