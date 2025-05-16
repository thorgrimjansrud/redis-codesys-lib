---
description: Method
---

# SUBSCRIBERBASE

## Codesys usage

Subscribe channel(s)  

```
VAR	
	FbRedis : FbRedis;
	IClientSub : ISubscriber := FbRedis;
	xSubscribe : BOOL;
	asSubscriptions : ARRAY [1..gcMAX_SUBSCRIPTIONS] OF STRING(gcMAX_STRINGLENGHT);
	typSubResults : typSubResults;
	eStatusCode : eStatusCode;
END_VAR
```

```
eStatusCode := IClientSub.SubscriberBase(asChannel:= asSubscriptions, xAddChannel:= xSubscribe, typSubResults:= typSubResults);
```

## Note

Once the client enters the subscribed state it is not supposed to issue any other commands, except for additional SUBSCRIBE, SSUBSCRIBE, PSUBSCRIBE, UNSUBSCRIBE, SUNSUBSCRIBE, PUNSUBSCRIBE, PING, RESET and QUIT commands. However, if RESP3 is used (see HELLO) it is possible for a client to issue any commands while in subscribed state.

New subscription s can only be executed if the asSubscriptions-fields are empty. To prevent writing faulty values into asSubscriptions a good practice is to use retain persistent variables for typSubResults and check these before calling method. Values will also be saved in case of reset etc.


