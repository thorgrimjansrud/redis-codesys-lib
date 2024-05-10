---
description: Method
---

# PUBLISH

## Codesys usage

Posts a message to the given channel:

```
VAR	
	RedisClient : FbRedis;
	Redis : IClient := RedisClient;
	xTrigger : BOOL;
	sResult : STRING(gcMAX_STRINGLENGHT);
	sPubChannel: STRING(gcMAX_STRINGLENGHT);
	sPubMessage: STRING(gcMAX_STRINGLENGHT);
END_VAR
```

```
IF xTrigger THEN
	sResult := Redis.publish(psChannel:= ADR(sPubChannel), psMessage:= ADR(sPubMessage));
	IF typResult.sData <> '' THEN
		xTrigger := FALSE;
	END_IF
END_IF
```
