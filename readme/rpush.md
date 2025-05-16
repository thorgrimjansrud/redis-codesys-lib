---
description: Method
---

# RPUSH

## Codesys usage

Insert specified values at the end of the list stored at key:

```
VAR	
	FbRedis : FbRedis;
	IRedis : IClient := FbRedis;
	xTrigger : BOOL;
	sKey, sData : STRING;
	asElement : ARRAY [1..gcMAX_ELEMENT] OF STRING(gcMAX_STRINGLENGHT);
	eStatusCode : eStatusCode;
END_VAR
```

```
IF xTrigger THEN	
	eStatusCode := FbRedis.RPush(psKey:= ADR(sKey) , asElement:= asElement, sRetVal:= sData);
	IF sData <> '' and eStatusCode = 0 THEN
		xTrigger := FALSE;
	END_IF
END_IF
```
