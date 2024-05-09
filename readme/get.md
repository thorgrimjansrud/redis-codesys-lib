---
description: Method
---

# GET

## Codesys usage

Retrieves value from a key:

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
	sResult := Redis.Get(psKey:= ADR(sKey));
	IF sResult <> '' THEN
		xTrigger := FALSE;
	END_IF
END_IF	 
```
