FROM quay.io/centos/centos:stream10
ENV container=docker

RUN dnf -y --refresh install 'dnf-command(config-manager)' epel-release && \
    dnf config-manager --set-enabled crb && \
    dnf -y install dnf-utils python3 python3-devel sudo systemd && \
    dnf clean all

# hadolint ignore=DL3003,SC2086
RUN (cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == \
    systemd-tmpfiles-setup.service ] || rm -f $i; done); \
    rm -f /lib/systemd/system/multi-user.target.wants/*;\
    rm -f /etc/systemd/system/*.wants/*;\
    rm -f /lib/systemd/system/local-fs.target.wants/*; \
    rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
    rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
    rm -f /lib/systemd/system/basic.target.wants/*;\
    rm -f /lib/systemd/system/anaconda.target.wants/*;

CMD ["/usr/sbin/init"]

VOLUME ["/sys/fs/cgroup", "/tmp", "/run"]
