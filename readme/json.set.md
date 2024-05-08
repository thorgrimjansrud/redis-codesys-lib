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
	Redis : IJson := RedisClient;
END_VAR
```

```
IF xTrigSet THEN
	sResult := Redis.JsonSet(psKey:= ADR(sKey),psPath:= ADR(sRootPath),psValue:= ADR(sValue),xNX:= FALSE,xXX:= FALSE);
	IF sResult <> '' THEN
		xTrigSet := FALSE;
	END_IF
END_IF	 
```

