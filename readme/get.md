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
	sKey, sData : STRING(gcMAX_STRINGLENGHT);
	eStatusCode : eStatusCode;
END_VAR
```

```
IF xTrigger THEN	
	eStatusCode := IClient.Get(psKey:= ADR(sKey), sRetVal:= sData);
	IF sData <> '' and eStatusCode = 0 THEN
		xTrigger := FALSE;
	END_IF
END_IF 
```
