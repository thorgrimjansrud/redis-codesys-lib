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

Compiled in 3.5.19.20.

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

## Examples

* [WagoSysDynamicIoMapping](readme/WagoSysDynamicIoMapping.md)
