---
description: Method
---

# HGET

## Codesys usage

The HGET method reads field and value stored at hash:

```
VAR	
	RedisClient : FbRedis;
	Redis : IClient := RedisClient;
END_VAR
```

```
IF xTrigHget THEN
 	 typResult := Redis.Hget(psKey:= ADR(sKey), psField:= ADR(sField));
  	IF sResult <> '' THEN
	   xTrigHget := FALSE;
  	END_IF
END_IF
```
