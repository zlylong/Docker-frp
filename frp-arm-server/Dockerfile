FROM golang:1.10

COPY . /go/src/github.com/fatedier/frp

RUN cd /go/src/github.com/fatedier/frp \
 && make \
 && mv bin/frpc /frpc \
 && make clean

WORKDIR /

EXPOSE 80 443 6000 7000 7500

COPY frpc_min.ini /bin/frp/conf/frpc.ini

VOLUME /bin/frp/conf

WORKDIR /bin/frp
ENTRYPOINT ./frpc -c ./conf/frpc.ini
ENTRYPOINT ["/frpc"]
