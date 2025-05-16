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
	sKey, sField, sData : STRING;
	eStatusCode : eStatusCode;
END_VAR
```

```
IF xTrigger THEN
	eStatusCode := IClient.Hget(psKey:= ADR(sKey), psField:= ADR(sField), sRetVal:= sData);
	IF sData <> '' and eStatusCode = 0 THEN
		xTrigger := FALSE;
	END_IF
END_IF
```
