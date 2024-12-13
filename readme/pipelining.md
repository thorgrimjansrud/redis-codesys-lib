---
description: Pipelining (v1.0.1.2)
---

# Optimze round trip times with pipelining

## Codesys usage

Redis pipelining is a technique for improving performance by issuing multiple commands at once without waiting for the response to each individual command.

```
VAR	
	FbRedis : FbRedis;
	IBase : IBase := FbRedis;
	IClient : IClient := FBRedis;
	IPipe : IPipe := FbRedis;
	xIsConnected, xIsPiped : BOOL;
    iAmount: INT;
    sChannel, sMessage : STRING(gcMAX_STRINGLENGHT);
    pasResultPub: POINTER TO ARRAY [1..gcMAX_ELEMENT] OF STRING(gcMAX_STRINGLENGHT);
END_VAR
```

```
xIsConnected := IBase.Connect(sHost:= '10.0.0.8', wPortNo:= 6379);
IF xIsConnected THEN
	// Amount of piped telegrams
	iAmount := 50;
	// Start pipe
	xIsPiped := IPipe.Pipeline();	
	// Data
	FOR i:=1 TO iAmount DO
		sChannel := CONCAT('channel_', TO_STRING(i));
		sMessage := TO_STRING(i);
		IClient.publish(psChannel:= ADR(sChannel), psMessage:= ADR(sMessage));
	END_FOR
	// Execute pipe 
	pasResultExec := IPipe.Exec();
END_IF
```

## Note

Still under developement, limits not well documented at this point.
