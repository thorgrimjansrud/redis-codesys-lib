---
description: Method
---

# PSUBSCRIBE

## Codesys usage

Subscribes the client to the given patterns. Subscriber needs to run. Feedback in atypSubResult:  

```
VAR	
	RedisSubscriber : FbRedis;
	RedisSub : ISubscriber := RedisSubscriber; 
	xSubConnected, xPSubscribe : BOOL;
	sIP : STRING; 
	wDefaultPort : WORD := 6379;
	asSubscriptions :  ARRAY [1..gcMAX_SUBSCRIPTIONS] OF STRING(gcMAX_STRINGLENGHT);
	atypSubResult : ARRAY [1..gcMAX_SUBSCRIPTIONS] OF typSubResult;
END_VAR
```

```
xSubConnected := RedisSub.connect(sServer:= sIP, wPortNo:= wDefaultPort, xUnix:=FALSE);
IF xSubConnected THEN
	atypSubResult := RedisSub.SubscriberBase(asChannel:= asSubscriptions);
	RedisSub.PSubscribe(asChannel:= asSubscriptions, xTrigger:= xPSubscribe);
END_IF
```

