---
description: Redis Codesys client
---

# redis-codesys-lib

## ! <mark style="color:red;">Experimental !</mark>

## About

A [CoDeSys ](https://www.codesys.com/)client for [Redis, ](https://redis.io/)[KeyDB](https://docs.keydb.dev) and [DragonflyDB](https://www.dragonflydb.io/). Description how to install [here ](https://help.codesys.com/webapp/\_cds\_adding\_libraries\_to\_repository;product=codesys;version=3.5.17.0).

### CoDeSys

Compiled in 3.5.19.2

### Known issues

Some devices are not supporting CmpSocketUnix library. 
Streams and timeseries have som missing features.

## Version
Current version is 1.0.0.11 ([History](readme/history.md))

## Supported commands

* [CONNECT](readme/connect.md)
* [GET](readme/get.md)
* [SET](readme/set.md)
* [HSET](readme/hset.md)
* [HGET](readme/hget.md)
* [HGETALL](readme/hgetall.md)
* [EXCISTS](readme/excists.md)
* [PUBLISH](readme/publish.md)
* [SUBSCRIBE](readme/subscribe.md)
* [UNSUBSCRIBE](readme/unsubscribe.md)
* [PSUBSCRIBE](readme/psubscribe.md)
* [PUNSUBSCRIBE](readme/punsubscribe.md)
* [JSON.SET](readme/json.set.md)
* [LPUSH](readme/lpush.md)
* [RPUSH](readme/rpush.md)
* [LPOP](readme/lpop.md)
* [XADD](readme/xadd.md)
* [XREAD](readme/xread.md)
* [TSCREATE](readme/tscreate.md)
* [TSADD](readme/tsadd.md)

## CRG-Stack

Stack can be installed with docker compose (docker-folder). Before you start, check paths in the docker compose file.

Redis configuration:
```
wget -O redis.conf https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/main/docker/redis.conf --no-check-certificate
```
Note: Seems like redis/redis-stack-server sends PCP (Performance Co-Pilot) on localhost:6379 so port is here changed to 9001.

Compose file:
```
wget -O docker-compose.yml https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/main/docker/docker-compose.yml --no-check-certificate
```
Socket access for Grafana:
```
sudo chmod ugo+rw /tmp/redis.sock
```

We can now connect to Redis UI on http://IP:5540 and configure database connection on 127.0.0.1:9001.
Grafana is availible on http://IP:3000 with Redis datasource on unix socket.

## Examples

* [WagoSysDynamicIoMapping](readme/WagoSysDynamicIoMapping.md)
