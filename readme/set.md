---
description: Method
---

# SET

## Codesys usage

Writes key and value:

```
VAR	
	RedisClient : FbRedis;
	Redis : IClient := RedisClient;
	xTrigger : BOOL;
	sResult, sKey, sValue : STRING;
	typSetOptions : typSetOptions;
END_VAR
```

```
IF xTrigger THEN	
	typSetOptions.uliEX := 3; // E.g. set the expire time to 3 seconds.
	sResult := Redis.set(psKey:= ADR(sKey), psValue:= ADR(sValue), ptypOptions:= ADR(typSetOptions));
	IF sResult <> '' THEN
		xTrigger := FALSE;
	END_IF
END_IF	 	 
```

> Limited to 1 pair.
