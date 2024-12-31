---
description: Method
---

# JSON.SET

RedisJSON must be installed.

## Codesys usage

Set the JSON value at path in key:

```
VAR
	FbRedis : FbRedis;
	IRedis : IJson := FbRedis;
	xTrigger, xNX, xXX : BOOL;
	sResult, sKey, sRootPath : STRING;
	sValue : STRING(gcMAX_STRINGLENGHT);
END_VAR
```

```
IF xTrigger THEN
	sRootPath := WORD_AS_STRING(W:= 16#24, ORDER:= FALSE); // E.g. we can use the util.lib to insert default root $
	sResult := IRedis.JsonSet(psKey:= ADR(sKey),psPath:= ADR(sRootPath),psValue:= ADR(sValue),xNX:= xNX,xXX:= xXX);
	IF sResult <> '' THEN
		xTrigger := FALSE;
	END_IF
END_IF 
```

## Note sRootPath

When a dollar sign '$' is in a string literal, the following two characters are interpreted as a hexadecimal code according to the coding in ISO/IEC 8859-1. This means $n$r is new line and linebreak. Two dollar '$$' is a dollar '$'.

