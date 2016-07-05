FROM alpine:3.4

MAINTAINER cheminlin@cepave.com

ENV WORKDIR=/home/openfalcon DOCKERDIR=docker/alpine CONFIGDIR=/home/openfalcon/config

# Set timezone, bash, config dir
# Set alias in the case of user want to execute control in their terminal
RUN \
  apk add --no-cache tzdata bash \
  && cp /usr/share/zoneinfo/Asia/Taipei /etc/localtime \
  && echo "Asia/Taipei" > /etc/timezone \
  && echo "alias ps='pstree'" > ~/.bashrc \
  && mkdir -p $WORKDIR/logs

# Install Open-Falcon
RUN apk add --no-cache ca-certificates git iproute2
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
