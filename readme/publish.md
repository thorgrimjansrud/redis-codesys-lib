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
	sResult : STRING(gcMAX_STRINGLENGHT);
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
