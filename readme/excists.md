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
	asKey: ARRAY[1..3] OF STRING(gcMAX_STRINGLENGHT); 
END_VAR
```

```
IF xTrigger THEN	
	sResult := Redis.exists(asKey:= asKey);
	IF TO_INT(sResult) > 0 THEN
		xTrigger := FALSE;
	END_IF
END_IF
```
