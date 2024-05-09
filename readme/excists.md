---
description: Method
---

# EXCISTS

## Codesys usage

Checks if the key excists or not:

```
VAR	
	RedisClient : FbRedis;
	Redis : IClient := RedisClient;
	xTrigger : BOOL;
	sResult, sKey : STRING;
END_VAR
```

```
IF xTrigger THEN	
	sResult := Redis.exists(asKey:= asKey);
	IF TO_INT(sResult) > 0 THEN
		xTrigger := FALSE;
	END_IF
END_IFF
```
