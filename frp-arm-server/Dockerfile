FROM arm32v7/ubuntu:latest

ARG FRP_VERSION=0.20.0
CMD ["/bin/bash"]
RUN /bin/bash -c apt update \
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

COPY frpc_min.ini /var/frp/conf/frpc.ini

VOLUME /var/frp/conf

WORKDIR /var/frp
ENTRYPOINT ./frpc -c ./conf/frpc.ini
