---
description: Method
---

# SET

## Codesys usage

Writes key and value:

```
VAR	
	FbRedis : FbRedis;
	IRedis : IClient := FbRedis;
	xTrigger : BOOL;
	sKey, sValue, sData : STRING(gcMAX_STRINGLENGHT);
	eStatusCode : eStatusCode;
	typOptions : typSetOptions;
END_VAR
```

```
IF xTrigger THEN	
	typSetOptions.uliEX := 3; // E.g. set the expire time to 3 seconds.
	eStatusCode := IClient.Set(psKey:= ADR(sKey), psValue:= ADR(sValue), ptypOptions:= ADR(typOptions), sRetVal:= sData);
	IF sData <> '' and eStatusCode = 0 THEN
		xTrigger := FALSE;
	END_IF
END_IF 	 
```

## Note

Limited to 1 pair.
