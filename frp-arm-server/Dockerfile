FROM arm64v8/ubuntu:18.04

ARG FRP_VERSION=0.20.0

RUN apt update \
    && apt install -y wget

WORKDIR /tmp
RUN set -x \
    && wget https://github.com/fatedier/frp/releases/download/v${FRP_VERSION}/frp_${FRP_VERSION}_linux_arm.tar.gz \
    && tar -zxf frp_${FRP_VERSION}_linux_arm.tar.gz \
    && mv frp_${FRP_VERSION}_linux_arm /var/frp \
    && mkdir -p /var/frp/conf \
    && apt remove -y wget \
    && apt autoremove -y \
    && rm -rf /var/lib/apt/lists/*

COPY frps_min.ini /var/frp/conf/frps.ini

VOLUME /var/frp/conf
EXPOSE 80 443 7000 7500

WORKDIR /var/frp
ENTRYPOINT ./frps -c ./conf/frps.ini
