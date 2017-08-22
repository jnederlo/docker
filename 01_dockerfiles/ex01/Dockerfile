FROM	debian



RUN		apt-get update && \
		apt-get install bzip2 -y && \
		apt-get install wget -y && \
		mkdir -p opt/teamspeak && \
		useradd teamspeak

RUN		wget http://dl.4players.de/ts/releases/3.0.13.8/teamspeak3-server_linux_amd64-3.0.13.8.tar.bz2 -O /tmp/teamspeak.tar.bz2 && \
		tar jxf /tmp/teamspeak.tar.bz2 -C /opt/teamspeak && \
		rm -f /tmp/teamspeak.tar.bz2

WORKDIR	opt/teamspeak/teamspeak3-server_linux_amd64

RUN		mkdir /data

VOLUME	["/data"]

USER	teamspeak

ENTRYPOINT	["sh", "ts3server_minimal_runscript.sh"]

EXPOSE	9987/udp
EXPOSE	30033
EXPOSE	10011
