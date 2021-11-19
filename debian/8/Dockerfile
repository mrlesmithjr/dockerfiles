FROM debian:8
ENV container docker

RUN apt-get update && \
    apt-get install -y --no-install-recommends python sudo systemd && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

CMD ["/lib/systemd/systemd"]

VOLUME ["/sys/fs/cgroup", "/tmp", "/run"]
