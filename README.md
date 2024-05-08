---
description: Redis Codesys client
---

# redis-codesys

## ! <mark style="color:red;">Experimental !</mark>

## About

A [CoDeSys ](https://www.codesys.com/) client for [Redis ](https://redis.io/) and [KeyDB](https://docs.keydb.dev/). Should run on all CoDeSys 3.5 supported plattforms.

## Prerequisite

### Database

A Redis or KeyDB database.

### CoDeSys libraries

All necesarry libraries are availible in a standard CoDeSys installation. Add these to your project:

* Standard
* StringUtils
* TCP
* Util
* CmpSocketUnix

## Supported commands

* [CONNECT](readme/connect.md)
* [GET](readme/get.md)
* [SET](readme/set.md)
* [HSET](readme/hset.md)
* [HGET](readme/hget.md)
* [EXCISTS](readme/excists.md)
* [PUBLISH](readme/publish.md)
* [SUBSCRIBE](readme/subscribe.md)
* [JSON.SET](readme/json.set.md)

