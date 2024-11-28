---
description: Method
---

# PUNSUBSCRIBE

## Codesys usage

Unsubscribes the client from the given patterns, or from all of them if none is given. Subscriber needs to run. Feedback in atypSubResult:

```
VAR	
	FbRedis : FbRedis;
	IRedis : ISubscriber := FbRedis;
	xSubConnected, xPSubscribe, xPUnsubscribe: BOOL;
	sIP : STRING; 
	wDefaultPort : WORD := 6379;
	asSubscriptions, asPUnsubscribe :  ARRAY [1..gcMAX_SUBSCRIPTIONS] OF STRING(gcMAX_STRINGLENGHT);
	atypSubResult : ARRAY [1..gcMAX_SUBSCRIPTIONS] OF typSubResult;
END_VAR
```

```
IF xSubConnected THEN
	atypSubResult := IRedis.SubscriberBase(asChannel:= asSubscriptions, xAddChannel:= xSubscribe);
	IRedis.PUnSubscribe(asChannel:= asPunsubscribe, xTrigger:= xPUnsubscribe);
END_IF
```

## Note

Once the client enters the subscribed state it is not supposed to issue any other commands, except for additional SUBSCRIBE, SSUBSCRIBE, PSUBSCRIBE, UNSUBSCRIBE, SUNSUBSCRIBE, PUNSUBSCRIBE, PING, RESET and QUIT commands. However, if RESP3 is used (see HELLO) it is possible for a client to issue any commands while in subscribed state.