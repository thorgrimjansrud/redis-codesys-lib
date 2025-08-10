---
description: Redis Codesys client
---

# redis-codesys-lib

## About

[CoDeSys ](https://www.codesys.com/)client for [Redis, ](https://redis.io/)[KeyDB](https://docs.keydb.dev) and [DragonflyDB](https://www.dragonflydb.io/). Description how to install [here ](https://help.codesys.com/webapp/_cds_adding_libraries_to_repository;product=codesys;version=3.5.17.0).

### CoDeSys

Compiled in 3.5.20.50.

In the source library conditional pragmas are used to compile two binaries "redis" and "redis-no-unixsocket". This is described in FbRedis variable list.

Test Driven Development (TDD) in PLC\_PRG.&#x20;

## Supported commands

* [CONNECT](readme/connect.md)
* [GET](readme/get.md)
* [SET](readme/set.md)
* [HSET](readme/hset.md)
* [HGET](readme/hget.md)
* [HGETALL](readme/hgetall.md)
* [LPUSH](readme/lpush.md)
* [RPUSH](readme/rpush.md)
* [LPOP](readme/lpop.md)
* [PUBLISH](readme/publish.md)
* [SUBSCRIBERBASE](readme/subscriberBase.md)
* [UNSUBSCRIBE](readme/unsubscribe.md)
* [PSUBSCRIBE](readme/psubscribe.md)
* [PUNSUBSCRIBE](readme/punsubscribe.md)
* [EXCISTS](readme/excists.md)
* [JSON.SET](readme/json.set.md)
* [JSON.GET](readme/json.get.md)
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

We can now connect to Redis UI on http://IP:5540 and configure database connection on 127.0.0.1:9001.\
Grafana is availible on http://IP:3000 with Redis datasource on unix socket.

## Examples

* [WagoSysDynamicIoMapping](readme/WagoSysDynamicIoMapping.md)
* [Pipelining](readme/pipelining.md)
* [Blocking](readme/blocking.md)

## Raw Links for AI  

CONNECT: https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/refs/heads/main/readme/excists.md  
GET: https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/refs/heads/main/readme/get.md  
SET: https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/refs/heads/main/readme/set.md  
HSET: https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/refs/heads/main/readme/hset.md  
HGET: https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/refs/heads/main/readme/hget.md  
HGETALL: https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/refs/heads/main/readme/hgetall.md  
LPUSH: https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/refs/heads/main/readme/lpush.md  
RPUSH: https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/refs/heads/main/readme/rpush.md  
LPOP: https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/refs/heads/main/readme/lpop.md  
PUBLISH: https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/refs/heads/main/readme/publish.md  
SUBSCRIBERBASE: https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/refs/heads/main/readme/subscriberBase.md  
UNSUBSCRIBE: https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/refs/heads/main/readme/unsubscribe.md  
PSUBSCRIBE: https://github.com/thorgrimjansrud/redis-codesys-lib/blob/main/readme/psubscribe.md  
PUNSUBSCRIBE: https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/refs/heads/main/readme/punsubscribe.md   
EXCISTS: https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/refs/heads/main/readme/excists.md  
JSON.SET: https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/refs/heads/main/readme/json.set.md  
JSON.GET: https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/refs/heads/main/readme/json.get.md  
XADD: https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/refs/heads/main/readme/xadd.md  
XREAD: https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/refs/heads/main/readme/xread.md  
TSCREATE: https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/refs/heads/main/readme/tscreate.md  
TSADD: https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/refs/heads/main/readme/tsadd.md  

WagoSysDynamicIoMapping: https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/refs/heads/main/readme/WagoSysDynamicIoMapping.md  
Pipelining: http://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/refs/heads/main/readme/pipelining.md  
Blocking: https://raw.githubusercontent.com/thorgrimjansrud/redis-codesys-lib/refs/heads/main/readme/blocking.md  



