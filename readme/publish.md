---
description: Method
---

# PUBLISH

## Codesys usage

Posts a message to the given channel:

```
VAR	
	FbRedis : FbRedis;
	IRedis : IClient := FbRedis;
	asRetValue : ARRAY [1..gcMAX_ELEMENT] OF STRING(gcMAX_STRINGLENGHT);
	sPubChannel: STRING(gcMAX_STRINGLENGHT);
	sPubMessage: STRING(gcMAX_STRINGLENGHT);
	eStatusCode : eStatusCode;
END_VAR
```

```

eStatusCode := IClient.Publish(psChannel:= ADR(sChannel), psMessage:= ADR(sMessage), asRetVal:= asRetValue);
IF asRetValue[1] <> '' AND eStatusCode = 0 THEN
	asRetValue[1] := '';
END_IF 

```

## Note

Returns the number of clients that the message was sent to in ARRAY [1].
if message was piped, returns answer of [1..gcMAX_ELEMENT] that was piped.