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
	asElement : ARRAY [1..gcMAX_HASH] OF STRING(gcMAX_STRINGLENGHT)
END_VAR
```

```
asElement := IRedis.LPop(psKey:= ADR(sKey), uiCount:= uiCount, xTrigger:= xTrigger);
```
