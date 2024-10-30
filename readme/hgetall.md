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
IF xTrigger THEN
 	sResult := Redis.Hget(psKey:= ADR(sKey), psField:= ADR(sField));
  	IF sResult <> '' THEN
	   xTrigger := FALSE;
  	END_IF
END_IF
```
