---
description: Method
---

# HGET

## Codesys usage

Reads field and value stored at hash:

```
VAR	
	FbRedis : FbRedis;
	IRedis : IClient := FbRedis;
	xTrigger : BOOL;
	sResult, sKey, sField : STRING;
END_VAR
```

```
IF xTrigger THEN
 	sResult := IRedis.Hget(psKey:= ADR(sKey), psField:= ADR(sField));
  	IF sResult <> '' THEN
	   xTrigger := FALSE;
  	END_IF
END_IF
```
