FROM ubuntu:17.10
RUN apt-get update && apt-get install -y git curl ca-certificates unzip xz-utils && \
    curl -sL https://github.com/rancher/machine-package/releases/download/v0.12.2/docker-machine.tar.gz | tar xvzf - -C /usr/bin && \
    useradd rancher && \
    mkdir -p /var/lib/rancher/etcd /var/lib/cattle && \
    chown -R rancher /var/lib/rancher /var/lib/cattle /usr/local/bin
VOLUME /var/lib/rancher
ENV ETCD_ARGS "--data-dir /var/lib/rancher/etcd"
USER rancher
WORKDIR /var/lib/rancher
COPY rancher /usr/bin/
ENTRYPOINT ["rancher", "--k8s-mode=exec"]