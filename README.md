# docker-openfalcon-backend

## Build

Enter the following command in the repo directory.

```
$ docker build -t backend -f docker/ubuntu/Dockerfile .
```

## Run

### Basic Run

Run OpenFalcon agent

```
$ docker run -d -p 1988:1988 backend agent
```

Port of OpenFalcon components

+ agent:      1988
+ aggregator: 6055
+ fe:         1234 1235
+ graph:      6070 6071
+ hbs:        6030 6031
+ judge:      6080 6081
+ nodata:     6090
+ query:      9966
+ sender:     6066
+ task:       8002
+ transfer:   6060 8433


### Advanced Run

+ Self-defined configurations

```
$ docker run -d -p 1988:1988 -v config:/home/openfalcon/config backend agent
```
