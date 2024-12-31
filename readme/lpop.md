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
	pasElement : POINTER TO ARRAY [1..gcMAX_ELEMENT] OF STRING(gcMAX_STRINGLENGHT)
END_VAR
```

```
pasElement := IRedis.LPop(psKey:= ADR(sKey), uiCount:= uiCount, xTrigger:= xTrigger);
```
