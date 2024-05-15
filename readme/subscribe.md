---
description: Method
---

# SUBSCRIBE

## Codesys usage

Subscribe channel(s):  

```
VAR	
	RedisSubscriber : FbRedis;
	RedisSub : ISubscriber := RedisSubscriber;
	xSubConnected, xSubscribe : BOOL;
	sIP : STRING; 
	wDefaultPort : WORD := 6379;
	asSubscriptions :  ARRAY [1..gcMAX_SUBSCRIPTIONS] OF STRING(gcMAX_STRINGLENGHT);
	atypSubResult : ARRAY [1..gcMAX_SUBSCRIPTIONS] OF typSubResult;
END_VAR
```

```
xSubConnected := RedisSub.connect(sServer:= sIP, wPortNo:= wDefaultPort, xUnix:=FALSE);
IF xSubConnected THEN
	atypSubResult := RedisSub.subscribe(asChannel:= asSubscriptions, xTrigger:= xSubscribe);
END_IF
```

