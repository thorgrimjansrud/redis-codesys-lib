---
description: Method
---

# PUBLISH

## Codesys usage

Posts a message to the given channel:

```
VAR	
	FbRedis : FbRedis;
	IRedis : IClient := FbRedis;
	xTrigger : BOOL;
	sResult : POINTER TO ARRAY [1..gcMAX_ELEMENT] OF STRING(gcMAX_STRINGLENGHT);
	sPubChannel: STRING(gcMAX_STRINGLENGHT);
	sPubMessage: STRING(gcMAX_STRINGLENGHT);
END_VAR
```

```
IF xTrigger THEN
	sResult := IRedis.publish(psChannel:= ADR(sPubChannel), psMessage:= ADR(sPubMessage));
	IF sResult <> '' THEN
		xTrigger := FALSE;
	END_IF
END_IF
```

## Note

Returns the number of clients that the message was sent to in ARRAY [1].
if message was piped, returns answer of [1..gcMAX_ELEMENT] that was piped.