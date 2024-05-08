---
description: Method
---

# PUBLISH

## Codesys usage

The PUBLISH method posts a message to the given channel:

```
VAR	
	RedisClient : FbRedis;
	Redis : IClient := RedisClient;
END_VAR
```

```
IF xTrigPub THEN
	typResult := Redis.publish(psChannel:= ADR(sChannel), psMessage:= ADR(sMessage));
	IF typResult.sData <> '' THEN
		xTrigPub := FALSE;
	END_IF
END_IF
```
