FROM alpine:3.14
ENV container docker

RUN apk --no-cache add openrc && \
    apk --no-cache add python3 sudo && \
    sed -i 's/^tty/#tty/g' /etc/inittab && \
    rm -rf /var/log/*

VOLUME [ "/run" ]

CMD ["/sbin/init"]
