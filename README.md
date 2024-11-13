---
description: Redis Codesys client
---

# redis-codesys-lib

## ! <mark style="color:red;">Experimental !</mark>

## About

A [CoDeSys ](https://www.codesys.com/)client for [Redis, ](https://redis.io/)[KeyDB](https://docs.keydb.dev) and [DragonflyDB](https://www.dragonflydb.io/). Description how to install [here ](https://help.codesys.com/webapp/\_cds\_adding\_libraries\_to\_repository;product=codesys;version=3.5.17.0).

## Prerequisite

### Database

E.g. Redis in Docker [here ](https://redis.io/docs/latest/operate/oss\_and\_stack/install/install-stack/docker/):

```
docker run -d --restart unless-stopped --name redis-stack -p 6379:6379 -p 8001:8001 redis/redis-stack:latest
```

Use Redis Insight (localhost:8001/) to monitor actions.

### CoDeSys

Compiled in 3.5.19.7

### Known issues

Some devices are not supporting CmpSocketUnix library. Streams have som missing features.

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

## About the CODESYS interfaces 
Redis methods are spread over to different Interfaces. IBase.Connect is mandatory for the connection. In addition you can choose interfaces besed on what functioality you need. E.g. you connect with interface IBase and read streams with interface IStream. In this case you need to instantiate both interfaces.

## Codesys-Redis-Grafana (CRG-Stack)

We can test the CODESYS library with Redis docker container on ARM64/AMD64 devices. Grafana is also added.
Stack is installed with docker compose. Before you start, check paths in the docker compose file.

Redis configuration
```
wget -O redis.conf https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/main/docker/redis.conf --no-check-certificate
```
CRG stack:
```
wget -O docker-compose.yml https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/main/docker/docker-compose.yml --no-check-certificate
```
Compose:
```
docker-compose up
```
Permit docker access (WORKAROUND):
```
sudo chmod ugo+rw /tmp/redis.sock
```

## Examples

* [WagoSysDynamicIoMapping](readme/WagoSysDynamicIoMapping.md)
