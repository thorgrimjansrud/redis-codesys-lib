---
description: Method
---

# HSET

## Codesys usage

The HSET method writes field and value stored at hash:

```
VAR	
	RedisClient : FbRedis;
	Redis : IClient := RedisClient;
END_VAR
```

```
IF xTrigHset THEN
	typResult := Redis.hset(psKey:= ADR(sKey), psField:= ADR(sField), psValue:= ADR(sValue));
	IF typResult.sData = '0' OR sResHset = '1' THEN
		xTrigHset := FALSE;
	END_IF
END_IF
```

> Limited to 1 field per hash
