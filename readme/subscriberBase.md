---
description: Method
---

# SUBSCRIBERBASE

## Codesys usage

Subscribe channel(s)  

```
VAR	
	FbRedis : FbRedis;
	IRedis : ISubscriber := FbRedis;
	xSubConnected, xSubscribe : BOOL;
	asSubscriptions :  ARRAY [1..gcMAX_SUBSCRIPTIONS] OF STRING(gcMAX_STRINGLENGHT);
	ptypSubResult : pointer to typSubResults;
END_VAR
```

```
ptypSubResults := IRedis.SubscriberBase(asChannel:= asSubscriptions, xAddChannel:= xSubscribe);
```

## Note

Once the client enters the subscribed state it is not supposed to issue any other commands, except for additional SUBSCRIBE, SSUBSCRIBE, PSUBSCRIBE, UNSUBSCRIBE, SUNSUBSCRIBE, PUNSUBSCRIBE, PING, RESET and QUIT commands. However, if RESP3 is used (see HELLO) it is possible for a client to issue any commands while in subscribed state.

Because of this we block for other methods writing to instance with declaring seperate FB for subscriber.
