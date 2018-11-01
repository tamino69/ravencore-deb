FROM ubuntu:xenial

ENV DEBIAN_FRONTEND noninteractive
ENV HOME /root
ENV TERM linux

RUN apt-get update && \
    apt-get upgrade -qy && \
    apt-get install -qy apt-transport-https curl git python-minimal && \
    curl https://deb.nodesource.com/node_10.x/pool/main/n/nodejs/nodejs_10.5.0-1nodesource1_amd64.deb > node.deb && \
    dpkg -i node.deb && \
    rm node.deb && \
RUN apt-get update && \
    apt-get -qy install python3 make build-essential devscripts dh-systemd
ADD ravencore/ /root/ravencore
RUN ( cd /root/ravencore && debuild -uc -us )
