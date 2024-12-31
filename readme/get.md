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
	sKey : STRING;
	psResult : pointer to STRING(gcMAX_STRINGLENGHT)
END_VAR
```

```
IF xTrigger THEN	
	psResult := IRedis.Get(psKey:= ADR(sKey));
	IF psResult^ <> '' THEN
		xTrigger := FALSE;
	END_IF
END_IF 
```
