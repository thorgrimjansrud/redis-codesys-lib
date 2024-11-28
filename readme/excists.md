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
	sResult, sKey : STRING;
	asKey: ARRAY[1..gcMAX_KEY] OF STRING(gcMAX_STRINGLENGHT); 
END_VAR
```

```
IF xTrigger THEN	
	sResult := IRedis.exists(asKey:= asKey);
	IF TO_INT(sResult) > 0 THEN
		xTrigger := FALSE;
	END_IF
END_IF
```
