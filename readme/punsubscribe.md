---
description: Method
---

# PUNSUBSCRIBE

## Codesys usage

Unsubscribes the client from the given patterns, or from all of them if none is given. Subscriber needs to run. Feedback in atypSubResult:

```
VAR	
	RedisSubscriber : FbRedis;
	RedisSub : ISubscriber := RedisSubscriber;
	xSubConnected, xPSubscribe, xPUnsubscribe: BOOL;
	sIP : STRING; 
	wDefaultPort : WORD := 6379;
	asSubscriptions, asPUnsubscribe :  ARRAY [1..gcMAX_SUBSCRIPTIONS] OF STRING(gcMAX_STRINGLENGHT);
	atypSubResult : ARRAY [1..gcMAX_SUBSCRIPTIONS] OF typSubResult;
END_VAR
```

```
xSubConnected := RedisSub.Connect(sServer:= sIP, wPortNo:= wDefaultPort, xUnix:=FALSE);
IF xSubConnected THEN
	atypSubResult := RedisSub.SubscriberBase(asChannel:= asSubscriptions, xTrigger:= xSubscribe);
	RedisSub.PSubscribe(asChannel:= asSubscriptions, xTrigger:= xPSubscribe);
	RedisSub.PUnSubscribe(asChannel:= asPunsubscribe, xTrigger:= xPUnsubscribe);
END_IF
```

