---
description: Method
---

# SUBSCRIBE

## Codesys usage

The SUBSCRIBE method subscribes to spedific channels:

```
VAR	
	RedisSubscriber : FbRedis;
	RedisSub : ISubscriber := RedisSubscriber; 
END_VAR
```

```
xSubConnected := RedisSub.connect('127.0.0.1', wPortNo:= 6379, xUnix:=TRUE);
IF xSubConnected THEN
	asSubscriptions[1] := 'weather';
	asSubscriptions[2] := 'sports';
	asSubscriptions[3] := 'news';
	atypSubResult := RedisSub.subscribe(asChannel:= asSubscriptions);
END_IF
```

