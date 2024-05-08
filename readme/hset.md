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
	sResult := Redis.Hset(psKey:= ADR(sKey), asField:= asField, asValue:= asValue);
	IF sResult <> '' THEN 
		xTrigHset := FALSE;
	END_IF
END_IF
```

> Limited to 1 field per hash
