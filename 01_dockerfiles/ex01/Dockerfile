# run docker with:
# docker run --rm -d -p 9987:9987/udp -p 11011:11011 -p 30033:30033 <img-name>

FROM debian

ENV TS3SERVER_LICENSE accept

ADD http://dl.4players.de/ts/releases/3.2.0/teamspeak3-server_linux_amd64-3.2.0.tar.bz2 ./cyka.tar.bz2

RUN apt-get update -y && \
	apt-get upgrade -y && \
	apt-get install -y bzip2 ca-certificates && \
	tar -xvf cyka.tar.bz2 && \
	rm cyka.tar.bz2

EXPOSE 9987/udp
EXPOSE 30033
EXPOSE 11011

CMD /teamspeak3-server_linux_amd64/ts3server_minimal_runscript.sh
