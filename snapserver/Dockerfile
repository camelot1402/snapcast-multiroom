FROM debian:9.0

ARG  snapcast_version=0.17.1
ENV  STREAM_NAME Snapserver

RUN  apt-get update \
  && apt-get install -y wget ca-certificates \
  && rm -rf /var/lib/apt/lists/*
RUN  wget https://github.com/badaix/snapcast/releases/download/v${snapcast_version}/snapserver_${snapcast_version}-1_amd64.deb
RUN  dpkg -i snapserver_${snapcast_version}-1_amd64.deb \
  ;  apt-get update \
  && apt-get -f install -y \
  && rm -rf /var/lib/apt/lists/*
RUN dpkg -i snapserver_${snapcast_version}-1_amd64.deb
RUN snapserver -v
RUN mkdir /fifo
COPY snapserver.conf /etc/snapserver
EXPOSE 1704 1705
#ENTRYPOINT ["/bin/bash","-c","source /etc/default/snapserver && snapserver $SNAPSERVER_OPTS"]
ENTRYPOINT ["snapserver"]
