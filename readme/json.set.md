---
description: Method
---

# JSON.SET

RedisJSON must be installed.

## Codesys usage

The JSON.SET method sets a Json object:

```
VAR
	RedisClient : FbRedis;
	RedisJson : IJson := RedisClient;
END_VAR
```

```
IF xTrigSet THEN
	typResult := RedisJson.JsonSet(psKey:= ADR(sKey), psPath:= ADR(sPath), psValue:= ADR(sValue), xNX:= FALSE, xXX:= FALSE);
	IF typResult.sData <> '' AND typResult.enuStatusCodes = 0 THEN
		xTrigSet := FALSE;
	ELSIF typResult.enuStatusCodes <> 0 THEN
		xTrigSet := FALSE;
	END_IF
END_IF	 
```

