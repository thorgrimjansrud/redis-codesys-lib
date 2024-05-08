---
description: Method
---

# SET

## Codesys usage

The SET method writes key and value:

```
VAR	
	RedisClient : FbRedis;
	Redis : IClient := RedisClient;
END_VAR
```

```
IF xTrigSet THEN
	sResult := Redis.set(psKey:= ADR(sKey), psValue:= ADR(sValue), ptypOptions:= ADR(typSetOptions));
	IF typResult.sData <> '' AND typResult.enuStatusCodes = 0 THEN
		xTrigSet := FALSE;
	ELSIF typResult.enuStatusCodes <> 0 THEN
		xTrigSet := FALSE;
	END_IF
END_IF	 	 
```

> Limited to 1 pair.
