FROM quay.io/centos/centos:stream8
ENV container=docker

RUN sed -i s/mirror.centos.org/vault.centos.org/g /etc/yum.repos.d/CentOS-*.repo && \
    sed -i s/^#.*baseurl=http/baseurl=http/g /etc/yum.repos.d/CentOS-*.repo && \
    sed -i s/^mirrorlist=http/#mirrorlist=http/g /etc/yum.repos.d/CentOS-*.repo

RUN dnf -y --refresh install 'dnf-command(config-manager)' https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm && \
    dnf config-manager --set-enabled powertools && \
    dnf -y install dnf-utils epel-next-release python3 python39-devel sudo systemd && \
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
