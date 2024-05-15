---
description: Method
---

# SUBSCRIBE

## Codesys usage

Unsubscribes to spesific channel(s). Subscriber needs to run. Feedback in atypSubResult:

```
VAR	
	RedisSubscriber : FbRedis;
	RedisSub : ISubscriber := RedisSubscriber;
	xSubConnected, xSubscribe : BOOL;
	sIP : STRING; 
	wDefaultPort : WORD := 6379;
	asSubscriptions, asUnsubscribe :  ARRAY [1..gcMAX_SUBSCRIPTIONS] OF STRING(gcMAX_STRINGLENGHT);
	atypSubResult : ARRAY [1..gcMAX_SUBSCRIPTIONS] OF typSubResult;
END_VAR
```

```
xSubConnected := RedisSub.Connect(sServer:= sIP, wPortNo:= wDefaultPort, xUnix:=FALSE);
IF xSubConnected THEN
	atypSubResult := RedisSub.subscribe(asChannel:= asSubscriptions, xTrigger:= xSubscribe);
	RedisSub.Unsubscribe(asChannel:= asUnsubscribe, xTrigger:= xUnsubscribe); 
END_IF
```

