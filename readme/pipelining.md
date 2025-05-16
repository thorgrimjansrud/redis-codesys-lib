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
    xIsPiped : BOOL;
    iAmount, iWaitingCycle: INT;
    sChannel, sMessage : STRING(gcMAX_STRINGLENGHT);
    asRetValue : ARRAY [1..gcMAX_ELEMENT] OF STRING(gcMAX_STRINGLENGHT);
	eStatusCode : eStatusCode;
	unRx : unRx;
END_VAR
```

```
// Amount of piped telegrams
iAmount := 5;

// Start pipe
xIsPiped := IPipe.Pipeline();	

// Data is i counter values. Wait until ready for new values.
IF xWait THEN
	FOR i:=1 TO iAmount DO
		sChannel := 'counter';
		sMessage := TO_STRING(iCounter);
		iCounter := iCounter + 1;
		// Buffer messages
		eStatusCode := IClient.Publish(psChannel:= ADR(sChannel), psMessage:= ADR(sMessage), asRetVal:= asRetValue);
	END_FOR
END_IF

// Execute pipe 
IPipe.Exec(asRetVal:= asRetValue);
IF asRetValue[1] <> '' AND asRetValue[2] <> '' AND asRetValue[3] <> '' AND asRetValue[4] <> '' AND asRetValue[5] <> '' THEN
	xWait := false;
ELSE
	xWait := true; 
END_IF
```

