FROM debian:10
ENV container docker

RUN apt-get update && \
    apt-get install -y --no-install-recommends python3 sudo systemd

CMD ["/lib/systemd/systemd"]

VOLUME ["/sys/fs/cgroup", "/tmp", "/run"]
