---
description: Method
---

# LPUSH

## Codesys usage

Insert specified values at the start of the list stored at key:

```
VAR	
	FbRedis : FbRedis;
	IRedis : IClient := FbRedis;
	xTrigger : BOOL;
	sKey : STRING;
	psResult : pointer to string(gcMAX_STRINGLENGHT);
	pasElement : pointe to ARRAY [1..gcMAX_ELEMENT] OF STRING(gcMAX_STRINGLENGHT)
END_VAR
```

```
IF xTrigger THEN	
	psResult := IRedis.LPush(psKey:= ADR(sKey), asElement:= asElement);
	IF psResult^ <> '' THEN 
		xTrigger := FALSE;
	END_IF
END_IF
```
