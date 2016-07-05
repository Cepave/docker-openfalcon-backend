FROM ubuntu:14.04.2

MAINTAINER minimum@cepave.com

ENV WORKDIR=/home/openfalcon DOCKERDIR=docker/ubuntu CONFIGDIR=/home/openfalcon/config

# Install Open-Falcon
RUN \
  apt-get update \
  && apt-get install -y ca-certificates git \
  && mkdir -p $WORKDIR/logs
ADD $DOCKERDIR/open-falcon.tar.gz $WORKDIR
RUN ln -sf $CONFIGDIR/api.json $WORKDIR/bin/fe/cfg.json

WORKDIR $WORKDIR
COPY $DOCKERDIR/run.sh $WORKDIR/

# Port
# agent:      1988
# aggregator: 6055
# fe:         1234 1235
# graph:      6070 6071
# hbs:        6030 6031
# judge:      6080 6081
# nodata:     6090
# query:      9966
# sender:     6066
# task:       8002
# transfer:   6060 8433
EXPOSE 1988 6055 1234 1235 6070 6071 6030 6031 6080 6081 6090 9966 6066 8002 6060 8433

# Start
ENTRYPOINT ["/bin/bash", "run.sh"]

