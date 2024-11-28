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
	xConnected: BOOL;
	sKey,sKey1, sKey2 : STRING;
	atypElements : array [1..2] of atypElements
	bGetAmountCnt : BYTE;
END_VAR
```

```
IF xConnected THEN
	atypElements := IRedis.HgetAll(psKey:= ADR(sKey));
END_IF
```

Or if we want several keys, something like:


```
IF xTrigger THEN
	IF bGetAmountCnt = 1 THEN
		sKey := 'sKey1';
		atypElements := IRedis.HgetAll(psKey:= ADR(sKey1));
		IF sKey1 = '' THEN
			RETURN;
		ELSE
			bGetAmountCnt := bGetAmountCnt + 1;
		END_IF
	END_IF
		
	IF bGetAmountCnt = 2 THEN
		sKey := 'sKey2';
		atypElements := IRedis.HgetAll(psKey:= ADR(sKey2));
		IF sKey2 = '' THEN
			RETURN;
		ELSE
			bGetAmountCnt := 0;
			xTrigger := false;
		END_IF
	END_IF
END_IF
```
