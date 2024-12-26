---
description: Method
---

# UNSUBSCRIBE

## Codesys usage

Unsubscribes to spesific channel(s). Subscriber needs to run. Feedback in atypSubResult:

```
VAR	
	FbRedis : FbRedis;
	IRedis : ISubscriber := FbRedis;
	xSubConnected, xSubscribe : BOOL;
	asSubscriptions, asUnsubscribe :  ARRAY [1..gcMAX_SUBSCRIPTIONS] OF STRING(gcMAX_STRINGLENGHT);
	patypSubResult : pointer to typSubResults;
END_VAR
```

```
IF xSubConnected THEN
	patypSubResult := IRedis.SubscriberBase(asChannel:= asSubscriptions, xTrigger:= xSubscribe);
	IRedis.Unsubscribe(asChannel:= asUnsubscribe, xTrigger:= xUnsubscribe); 
END_IF
```

## Note

Once the client enters the subscribed state it is not supposed to issue any other commands, except for additional SUBSCRIBE, SSUBSCRIBE, PSUBSCRIBE, UNSUBSCRIBE, SUNSUBSCRIBE, PUNSUBSCRIBE, PING, RESET and QUIT commands. However, if RESP3 is used (see HELLO) it is possible for a client to issue any commands while in subscribed state.