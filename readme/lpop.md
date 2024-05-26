---
description: Method
---

# LPOP

## Codesys usage

Removes and returns the first elements of the list stored at key:

```
VAR	
	RedisClient : FbRedis;
	Redis : IClient := RedisClient;
	xTrigger : BOOL;
	uiCount: uint;
	sKey : STRING;
	asElement : ARRAY [1..gcMAX_HASH] OF STRING(gcMAX_STRINGLENGHT)
END_VAR
```

```
asElement := Redis.LPop(psKey:= ADR(sKey), uiCount:= uiCount, xTrigger:= xTrigger);
```
