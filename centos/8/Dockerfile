FROM quay.io/centos/centos:stream8
ENV container docker

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

RUN dnf config-manager --set-enabled powertools && \
    dnf install -y --refresh epel-release python3 python39-devel sudo && \
    dnf clean all

CMD ["/usr/sbin/init"]

VOLUME ["/sys/fs/cgroup", "/tmp", "/run"]
