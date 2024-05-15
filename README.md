---
description: Redis Codesys client
---

# redis-codesys-lib

## ! <mark style="color:red;">Experimental !</mark>

## About

A [CoDeSys ](https://www.codesys.com/) client for [Redis ](https://redis.io/).
Description how to install [here ](https://help.codesys.com/webapp/_cds_adding_libraries_to_repository;product=codesys;version=3.5.17.0 ).

## Prerequisite

### Database

A Redis or KeyDB database.

### CoDeSys 

Compiled in 3.5.19.20 (SP19 patch 2).

### Known issues

Some devices are not supporting CmpSocketUnix library.
Poll me [here ](https://github.com/thorgrimjansrud/redis-codesys-lib/discussions/categories/general) for any questions.

## Supported commands

* [CONNECT](readme/connect.md)
* [GET](readme/get.md)
* [SET](readme/set.md)
* [HSET](readme/hset.md)
* [HGET](readme/hget.md)
* [EXCISTS](readme/excists.md)
* [PUBLISH](readme/publish.md)
* [SUBSCRIBE](readme/subscribe.md)
* [UNSUBSCRIBE](readme/unsubscribe.md)
* [JSON.SET](readme/json.set.md)

