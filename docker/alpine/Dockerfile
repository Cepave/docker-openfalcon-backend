FROM alpine:3.4

MAINTAINER cheminlin@cepave.com

ENV WORKDIR=/home DOCKERDIR=docker/alpine CONFIGDIR=/config

# Set timezone, bash, config dir
# Set alias in the case of user want to execute control in their terminal
RUN \
  apk add --no-cache tzdata bash \
  && cp /usr/share/zoneinfo/Asia/Taipei /etc/localtime \
  && echo "Asia/Taipei" > /etc/timezone \
  && echo "alias ps='pstree'" > ~/.bashrc

# Install Open-Falcon
RUN \
  apk add --no-cache ca-certificates git iproute2 curl jq \
  && mkdir -p $WORKDIR $CONFIGDIR
ADD $DOCKERDIR/open-falcon.tar.gz $WORKDIR
RUN \
  touch $CONFIGDIR/agent.json && \
  ln -sf $CONFIGDIR/agent.json /home/agent/config/cfg.json && \
  rm -f $CONFIGDIR/agent.json && \
  touch $CONFIGDIR/aggregator.json && \
  ln -sf $CONFIGDIR/aggregator.json /home/aggregator/config/cfg.json && \
  rm -f $CONFIGDIR/aggregator.json && \
  touch $CONFIGDIR/alarm.json && \
  ln -sf $CONFIGDIR/alarm.json /home/alarm/config/cfg.json && \
  rm -f $CONFIGDIR/alarm.json && \
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
  rm -f $CONFIGDIR/transfer.json && \
  touch $CONFIGDIR/nqm-mng.json && \
  ln -sf $CONFIGDIR/nqm-mng.json /home/nqm-mng/config/cfg.json && \
  rm -f $CONFIGDIR/nqm-mng.json && \
  touch $CONFIGDIR/api.json && \
  ln -sf $CONFIGDIR/api.json /home/api/config/cfg.json && \
  rm -f $CONFIGDIR/api.json

WORKDIR $WORKDIR
COPY $DOCKERDIR/run.sh $WORKDIR/
COPY docker-healthcheck /usr/local/bin/

# Port
# rpc:  10070
# http: 10080 10081
EXPOSE 10070 10080 10081

# Start
ENTRYPOINT ["/bin/bash", "run.sh"]
HEALTHCHECK --interval=60s --timeout=2s \
  CMD [ "bash", "docker-healthcheck" ]
