---
description: Method
---

# SUBSCRIBERBASE

## Codesys usage

Subscribe channel(s)  

```
VAR	
	FbRedis : FbRedis; // FB for subscriber, must not be used for other methods than subscribe.
	IRedis : ISubscriber := FbRedis;
	xSubConnected, xSubscribe : BOOL;
	asSubscriptions :  ARRAY [1..gcMAX_SUBSCRIPTIONS] OF STRING(gcMAX_STRINGLENGHT);
	atypSubResult : ARRAY [1..gcMAX_SUBSCRIPTIONS] OF typSubResult;
END_VAR
```

```
IF xSubConnected THEN
	atypSubResult := IRedis.SubscriberBase(asChannel:= asSubscriptions, xAddChannel:= xSubscribe);
END_IF
```

## Note

Once the client enters the subscribed state it is not supposed to issue any other commands, except for additional SUBSCRIBE, SSUBSCRIBE, PSUBSCRIBE, UNSUBSCRIBE, SUNSUBSCRIBE, PUNSUBSCRIBE, PING, RESET and QUIT commands. However, if RESP3 is used (see HELLO) it is possible for a client to issue any commands while in subscribed state.

Because of this we block for other methods writing to instance with declaring seperate FB for subscriber.
