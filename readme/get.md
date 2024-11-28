---
description: Method
---

# GET

## Codesys usage

Retrieves value from a key:

```
VAR	
	FbRedis : FbRedis;
	IRedis : IClient := FbRedis;
	xTrigger : BOOL;
	sResult, sKey : STRING;
END_VAR
```

```
IF xTrigger THEN	
	sResult := IRedis.Get(psKey:= ADR(sKey));
	IF sResult <> '' THEN
		xTrigger := FALSE;
	END_IF
END_IF	 
```
