---
description: Publish and Subscribe (v1.0.1.2)
---

# How to publish to multiple topics

## Codesys usage

The publish method takes only one topic and message. The example program shows one way of publishing to several topics within 1 program cycle.
Be aware of fan-out calling this method concurrently in a loop (e.g. WHILE sResult <> '' DO).
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
	ISub : ISubscriber := FbRedisSub; 
	// Vars
	sResult : STRING(gcMAX_STRINGLENGHT);
	asPubChannel, asSubscriptions : ARRAY [1..gcMAX_SUBSCRIPTIONS] OF STRING(gcMAX_STRINGLENGHT);
	atypSubResult : ARRAY [1..gcMAX_SUBSCRIPTIONS] OF typSubResult;
	asPubMessages : ARRAY [1..gcMAX_SUBSCRIPTIONS] OF STRING(gcMAX_STRINGLENGHT);
	xInit, xIsConnected, xIsConnectedSub, xAddSubscriberCh: BOOL;
	iSel, i: INT;
	oTim: TON;
END_VAR
```
PLC_PRG
```
// Connect Client and subscriber
xIsConnected := IBase.Connect(sHost:= '10.0.0.9', wPortNo:= 6379);
xIsConnectedSub := IBaseSub.Connect(sHost:= '10.0.0.9', wPortNo:= 6379);

IF xIsConnected THEN
	// Init publish and subscribe channels
	IF NOT xInit THEN
		FOR i:=1 TO 3 DO
			asPubChannel[i] := CONCAT('Triangle_', TO_STRING(i));
			asSubscriptions[i] := asPubChannel[i];
		END_FOR
		xInit := TRUE;
	END_IF
	
	// Subscribe
	atypSubResult := ISub.SubscriberBase(asChannel:= asPubMessages, xAddChannel:= xAddSubscriberCh);

	// Timer for trigger publish
	oTim(IN:= TRUE, PT:= T#1S);

	// Publish
	IF oTim.Q THEN
		// First
		IF iSel = 0 THEN 
			asPubMessages[1] := '111';
			sResult := IClient.publish(psChannel:= ADR(asSubscriptions[1]), psMessage:= ADR(asPubMessages[1]));
			IF sResult = '' THEN
				RETURN;
			END_IF
			iSel := 1;
		END_IF
		// Secund
		IF iSel = 1 THEN 
			asPubMessages[2] := '222';
			sResult := IClient.publish(psChannel:= ADR(asSubscriptions[2]), psMessage:= ADR(asPubMessages[2]));
			IF sResult = '' THEN
				RETURN;
			END_IF
			iSel := 2;
		END_IF
		// Third
		IF iSel = 2 THEN 
			asPubMessages[3] := '333';
			sResult := IClient.publish(psChannel:= ADR(asSubscriptions[3]), psMessage:= ADR(asPubMessages[3]));
			IF sResult = '' THEN
				RETURN;
			END_IF
			iSel := 0;
			oTim(IN:= FALSE, PT:= T#1S);
		END_IF
	END_IF
END_IF
```

