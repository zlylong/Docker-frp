FROM ubuntu:18.04
MAINTAINER keepwn <keepwn@gmail.com>

ARG FRP_VERSION=0.20.0

RUN apt update \
    && apt install -y wget

WORKDIR /tmp
RUN set -x \
    && wget https://github.com/fatedier/frp/releases/download/v${FRP_VERSION}/frp_${FRP_VERSION}_linux_amd64.tar.gz \
    && tar -zxf frp_${FRP_VERSION}_linux_amd64.tar.gz \
    && mv frp_${FRP_VERSION}_linux_amd64 /var/frp \
    && mkdir -p /var/frp/conf \
    && apt remove -y wget \
    && apt autoremove -y \
    && rm -rf /var/lib/apt/lists/*

COPY frpc_min.ini /var/frp/conf/frpc.ini

VOLUME /var/frp/conf

WORKDIR /var/frp
ENTRYPOINT ./frpc -c ./conf/frpc.ini
