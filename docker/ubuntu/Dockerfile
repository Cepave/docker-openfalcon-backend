FROM ubuntu:14.04.2

MAINTAINER minimum@cepave.com

ENV WORKDIR=/home DOCKERDIR=docker/ubuntu CONFIGDIR=/config

# Install Open-Falcon
RUN \
  apt-get update \
  && apt-get install -y ca-certificates git \
  && mkdir -p $WORKDIR $CONFIGDIR
ADD $DOCKERDIR/open-falcon.tar.gz $WORKDIR
RUN \
  touch $CONFIGDIR/aggregator.json && \
  ln -sf $CONFIGDIR/aggregator.json /home/aggregator/config/cfg.json && \
  rm -f $CONFIGDIR/aggregator.json && \
  touch $CONFIGDIR/fe.json && \
  ln -sf $CONFIGDIR/fe.json /home/fe/config/cfg.json && \
  rm -f $CONFIGDIR/fe.json && \
  touch $CONFIGDIR/graph.json && \
  ln -sf $CONFIGDIR/graph.json /home/graph/config/cfg.json && \
  rm -f $CONFIGDIR/graph.json && \
  touch $CONFIGDIR/hbs.json && \
  ln -sf $CONFIGDIR/hbs.json /home/hbs/config/cfg.json && \
  rm -f $CONFIGDIR/hbs.json && \
  touch $CONFIGDIR/judge.json && \
  ln -sf $CONFIGDIR/judge.json /home/judge/config/cfg.json && \
  rm -f $CONFIGDIR/judge.json && \
  touch $CONFIGDIR/nodata.json && \
  ln -sf $CONFIGDIR/nodata.json /home/nodata/config/cfg.json && \
  rm -f $CONFIGDIR/nodata.json && \
  touch $CONFIGDIR/query.json && \
  ln -sf $CONFIGDIR/query.json /home/query/config/cfg.json && \
  rm -f $CONFIGDIR/query.json && \
  touch $CONFIGDIR/sender.json && \
  ln -sf $CONFIGDIR/sender.json /home/sender/config/cfg.json && \
  rm -f $CONFIGDIR/sender.json && \
  touch $CONFIGDIR/task.json && \
  ln -sf $CONFIGDIR/task.json /home/task/config/cfg.json && \
  rm -f $CONFIGDIR/task.json && \
  touch $CONFIGDIR/transfer.json && \
  ln -sf $CONFIGDIR/transfer.json /home/transfer/config/cfg.json && \
  rm -f $CONFIGDIR/transfer.json

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

