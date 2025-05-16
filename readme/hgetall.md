---
description: Method
---

# HGETALL

## Codesys usage

Reads all fields and values stored at hash:

```
VAR
	FbRedis : FbRedis;
	IRedis : IClient := FbRedis;
	xTrigger: BOOL;
	sKey : STRING;
	patypElements : pointer to array [1..gcMAX_ELEMENT] of atypElement;
	eStatusCode : eStatusCode;
END_VAR
```

```
IF xTrigger THEN
	eStatusCode := IClient.HgetAll(psKey:= ADR(sKey), atypElement:= atypElement);
END_IF
```
