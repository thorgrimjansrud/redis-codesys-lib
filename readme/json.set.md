---
description: Method
---

# JSON.SET

RedisJSON must be installed.

## Codesys usage

Set the JSON value at path in key:

```
VAR
	RedisClient : FbRedis;
	Redis : IJson := RedisClient;
	xTrigger, xNX, xXX : BOOL;
	sResult, sKey, sRootPath : STRING;
	sValue : STRING(gcMAX_STRINGLENGHT);
END_VAR
```

```
IF xTrigger THEN
	sRootPath := WORD_AS_STRING(W:= 16#24, ORDER:= FALSE); // E.g. we can use the util.lib to insert default root $
	sResult := Redis.JsonSet(psKey:= ADR(sKey),psPath:= ADR(sRootPath),psValue:= ADR(sValue),xNX:= xNX,xXX:= xXX);
	IF sResult <> '' THEN
		xTrigger := FALSE;
	END_IF
END_IF 
```

