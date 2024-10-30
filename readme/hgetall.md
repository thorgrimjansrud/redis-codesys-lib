---
description: Method
---

# HGETALL

## Codesys usage

Reads all fields and values stored at hash:

```
VAR
  RedisClient : FbRedis;
  Redis : IClient := RedisClient;
  xConnected: BOOL;
  sKey : STRING;
END_VAR
```

```
xConnected := RedisStream.Connect(sServer:= sIP, wPortNo:= wDefaultPort, xUnix:=FALSE);
IF xConnected THEN
	atypElements := Redis.HgetAll(psKey:= ADR(sKey));
END_IF
```
