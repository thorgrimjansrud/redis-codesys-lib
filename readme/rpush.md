---
description: Method
---

# RPUSH

## Codesys usage

Insert specified values at the end of the list stored at key:

```
VAR	
	RedisClient : FbRedis;
	Redis : IClient := RedisClient;
	xTrigger : BOOL;
	sResult, sKey : STRING;
	asElement : ARRAY [1..gcMAX_HASH] OF STRING(gcMAX_STRINGLENGHT)
END_VAR
```

```
IF xTrigger THEN
	sResult := Redis.RPush(psKey:= ADR(sKey), asElement:= asElement);
	IF sResult <> '' THEN
		xTrigger := FALSE;
	END_IF
END_IF
```
