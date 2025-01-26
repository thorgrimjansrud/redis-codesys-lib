---
description: Method
---

# HSET

## Codesys usage

Write field and value stored at hash:

```
VAR	
	FbRedis : FbRedis;
	IRedis : IClient := FbRedis;
	xTrigger : BOOL;
	sResult, sKey : STRING;
	asField, asValue : ARRAY [1..gcMAX_HASH] OF STRING(gcMAX_STRINGLENGHT);
END_VAR
```

```
IF xTrigger THEN
	sResult := IRedis.Hset(psKey:= ADR(sKey), asField:= asField, asValue:= asValue);
	IF sResult <> '' THEN 
		xTrigger := FALSE;
	END_IF
END_IF
```


