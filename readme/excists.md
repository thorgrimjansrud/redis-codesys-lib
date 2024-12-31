---
description: Method
---

# EXCISTS

## Codesys usage

Checks if the keys excists or not:

```
VAR	
	FbRedis : FbRedis;
	IRedis : IClient := FbRedis;
	xTrigger : BOOL;
	sKey : STRING;
	psResult : POINTER TO STRING(gcMAX_STRINGLENGHT);
END_VAR
```

```
IF xTrigger THEN	
	psResult := IRedis.exists(asKey:= asKey);
	IF TO_INT(psResult^) > 0 THEN
		xTrigger := FALSE;
	END_IF
END_IF
```
