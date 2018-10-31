FROM ubuntu:xenial

ENV DEBIAN_FRONTEND noninteractive
ENV HOME /root
ENV TERM linux

RUN apt-get update && \
    apt-get upgrade -qy && \
    apt-get install -qy apt-transport-https curl git && \
    curl https://deb.nodesource.com/node_10.x/pool/main/n/nodejs/nodejs_10.5.0-1nodesource1_amd64.deb > node.deb && \
    dpkg -i node.deb && \
	rm node.deb && \
	echo 'deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.6 multiverse' | tee -a /etc/apt/sources.list.d/nodesource.list &&\
	apt-key adv --keyserver keyserver.ubuntu.com --recv 2930ADAE8CAF5059EE73BB4B58712A2291FA4AD5
RUN apt-get update && \
    apt-get -qy install python3 make build-essential devscripts dh-systemd mongodb-org
RUN npm install npm@latest -g
ADD ravencore/ /root/ravencore
RUN ( cd /root/ravencore && debuild -uc -us )
