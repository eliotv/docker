FROM debian

ENV TSV=3.0.13.6

RUN DEBIAN_FRONTEND=noninteractive \
apt-get -y update && \
apt-get -y install bzip2



ADD    http://dl.4players.de/ts/releases/${TSV}/teamspeak3-server_linux_amd64-${TSV}.tar.bz2 ./

RUN	tar jxf teamspeak3-server_linux_amd64-$TSV.tar.bz2 && \
	mv teamspeak3-server_linux_amd64 /opt/teamspeak && \
	rm teamspeak3-server_linux_amd64-$TSV.tar.bz2

ADD ./start /start
#RUN useradd teamspeak
RUN mkdir /data \
	mkdir /data/logs

EXPOSE 9987/udp
EXPOSE 30033
EXPOSE 10011

VOLUME ["/data"]
CMD ["/bin/bash", "/start"]

RUN docker run -p=9987:9987/udp -p=10011:10011 -p=30033:30033 -v=/mnt/teamspeak:/data ts
