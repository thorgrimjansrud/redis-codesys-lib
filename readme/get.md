---
description: Method
---

# GET

## Codesys usage

The GET method retrieves value from a key inside datastructure typResult:

```
VAR	
	RedisClient : FbRedis;
	Redis : IClient := RedisClient;
END_VAR
```

```
IF xTrigGet THEN
	typResult := Redis.Get(psKey:= ADR(sKey));
	IF typResult.sData <> '' AND typResult.enuStatusCodes = 0 THEN
		sData := typResult.sData;
		xTrigSet := FALSE;
	END_IF
END_IF	 
```
