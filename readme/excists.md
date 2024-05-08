---
description: Method
---

# EXCISTS

## Codesys usage

The EXCISTS method checks if the key excists or not:

```
VAR	
	RedisClient : FbRedis;
	Redis : IClient := RedisClient;
END_VAR
```

```
IF xTrigExists THEN	
	sResult := Redis.exists(asKey:= asKey);
	IF TO_INT(sResult) > 0 THEN
		xTrigExists := FALSE;
	ELSE
END_IF
```
