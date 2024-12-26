---
description: Publish and Subscribe (v1.0.1.4)
---

# How to publish to multiple topics

## Codesys usage

The publish method takes only one topic and message. The example program shows one way of publishing values at a fast phase.
```
PROGRAM PLC_PRG
VAR
	// Publisher
	FbRedis : FbRedis;
	IBase : IBase := FbRedis;
	IClient : IClient := FbRedis;
	// Subscriber
	FbRedisSub : FbRedis;
	IBaseSub : IBase := FbRedisSub; 
	ISubscriber : ISubscriber := FbRedisSub; 
	// Vars
	iCount : int;
	sResult, sPubChannel, sPubMessage : STRING(gcMAX_STRINGLENGHT);
	asSubscriptions : ARRAY [1..gcMAX_SUBSCRIPTIONS] OF STRING(gcMAX_STRINGLENGHT);
	ptypSubResults : POINTER TO typSubResults;
	pasResult : POINTER TO ARRAY [1..gcMAX_ELEMENT] OF STRING(gcMAX_STRINGLENGHT);
	xInit, xBusy, xIsConnected, xIsConnectedSub, xSubActive, xAddSubscriberCh, xPub, xOk, xPSubscribe, xPUnsubscribe: BOOL;
END_VAR
```
PLC_PRG
```
// Connect Client and subscriber
xIsConnected := IBase.Connect(sHost:= '10.0.0.9', wPortNo:= 6379);
xIsConnectedSub := IBaseSub.Connect(sHost:= '10.0.0.9', wPortNo:= 6379);

IF NOT xConnected AND xIsConnectedSub THEN
	RETURN;
END_IF


// Inhibit send of multiple of same values
IF NOT xInit THEN
	xAddSubscriberCh := TRUE;				// Add channel to subscriber
	asSubscriptions[1] := 'count';			// Channel name for subscribe
	sPubChannel := 'count';					// Channel name for publish
	ptypSubResults := ADR(typSubResults);	// Init pointer (only valid before subscriber runs)
	xInit := TRUE;
END_IF

// Check subscriber feedback and increase counter only if correct previous counter is recieved
IF xSubActive AND xBusy AND ptypSubResults^.atypSubMessage[1].sValue = sPubMessage THEN 
	iCount := iCount + 1;
	sPubMessage := TO_STRING(iCount);	
	xBusy := FALSE;
END_IF
				
// Publish new counter value after subscriber has recieved previous value.
// Because the publisher and subscriber runs at the sme device we must syncronize the pub-sub.
IF xSubActive AND NOT xBusy THEN
	xBusy := TRUE;
	pasResult := IRedis.Publish(psChannel:= ADR(sPubChannel), psMessage:= ADR(sPubMessage));
END_IF

// Subscriber
ptypSubResults := ISubscriber.SubscriberBase(asChannel:= asSubscriptions, xAddChannel:= xAddSubscriberCh);
IF ptypSubResults^.atypSubMessage[1].enuType = eMsgType.subscribe THEN
	xSubActive := TRUE;
END_IF
```

# How to pattern subscribe

```
// Connect Client and subscriber
xIsConnected := IBase.Connect(sHost:= '10.0.0.9', wPortNo:= 6379);
xIsConnectedSub := IBaseSub.Connect(sHost:= '10.0.0.9', wPortNo:= 6379);

IF NOT xConnected AND xIsConnectedSub THEN
	RETURN;
END_IF

IF xIsConnected AND xIsConnectedSub THEN
	// Subscriber must alway run (dont use "xSubscribe" if "psubscribe")
	ptypSubResults := ISubscriber.SubscriberBase(asChannel:= asSubscriptions, xAddChannel:= xAddSubscriberCh);
	// Check if recieve fromcorrect channel ''
	IF ptypSubResults^.atypSubMessage[1].sChannel = 'news' THEN
		IF ptypSubResults^.atypSubMessage[1].sValue <> '' THEN
			xOk := TRUE;
		ELSE
			xOk := FALSE;
		END_IF
	END_IF
	// PSubscribe
	asSubscriptions[1] := 'n?ws'; // e.g. n[e]ws, n[a]ws, n[o]ws..
	ISubscriber.PSubscribe(asChannel:= asSubscriptions, xTrigger:= xPSubscribe);
	// PUnsubscribe
	ISubscriber.PUnSubscribe(asChannel:= asSubscriptions, xTrigger:= xPUnsubscribe);
	// Publish
	sPubChannel := 'news';
	sPubMessage := 'this is great';
	IF xPub THEN
		pasResult := IClient.Publish(psChannel:= ADR(sPubChannel), psMessage:= ADR(sPubMessage));
		IF pasResult^[1] <> '' THEN
			xPub := FALSE;
		END_IF
	END_IF
END_IF
```