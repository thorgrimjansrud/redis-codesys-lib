---
description: Method
---

# LPOP

## Codesys usage

Removes and returns the first elements of the list stored at key:

```
VAR	
	FbRedis : FbRedis;
	IRedis : IClient := FbRedis;
	xTrigger : BOOL;
	uiCount: uint;
	sKey : STRING;
	asElement : ARRAY [1..gcMAX_ELEMENT] OF STRING(gcMAX_STRINGLENGHT);
	eStatusCode : eStatusCode;
END_VAR
```

```
IF xTrigger THEN	
	eStatusCode := IClient.LPop(psKey:= ADR(sKey), uiCount:= uiCount, asElement:= asElement);
	IF asElement[1] <> '' and eStatusCode = 0 THEN
		xTrigger := FALSE;
	END_IF
END_IF
```
