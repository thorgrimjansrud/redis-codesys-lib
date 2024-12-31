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
	sKey, sField : STRING;
	psResult : pointer to STRING(gcMAX_STRINGLENGHT)
END_VAR
```

```
IF xTrigger THEN	
	psResult := IRedis.Hget(psKey:= ADR(sKey), psField:= ADR(sField));
	IF psResult^ <> '' THEN
		xTrigger := FALSE;
	END_IF
END_IF
```
