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
	sKey, sValue : STRING;
	psResult : POINTER TO STRING(gcMAX_STRINGLENGHT);
	typSetOptions : typSetOptions;
END_VAR
```

```
IF xTrigger THEN	
	typSetOptions.uliEX := 3; // E.g. set the expire time to 3 seconds.
	psResult := IRedis.set(psKey:= ADR(sKey), psValue:= ADR(sValue), ptypOptions:= ADR(typSetOptions));
	IF psResult^ <> '' THEN
		xTrigger := FALSE;
	END_IF
END_IF 	 
```

## Note

Limited to 1 pair.
