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
	sKey, sData : STRING;
	asField, asValue : ARRAY [1..gcMAX_HASH] OF STRING(gcMAX_STRINGLENGHT);
	eStatusCode : eStatusCode;
END_VAR
```

```
IF xTrigger THEN
	eStatusCode := IClient.Hset(psKey:= ADR(sKey), asField:= asFields, asValue:= asValues, sRetVal:= sData);
	IF sData <> '' and eStatusCode = 0 THEN
		xTrigger := FALSE;
	END_IF
END_IF
```


