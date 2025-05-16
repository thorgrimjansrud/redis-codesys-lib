---
description: Blocking (v1.0.2.0)
---

# Optimze redis calls with method blocking

## Codesys usage

Default the library methods are non-blocking and will exit with or without any data. With blocking propterty you can
let the library wait for reply messages. The timeout parameter is set in the parameter list.

```
VAR	
    FbRedis : FbRedis;
    IBase : IBase := FbRedis;
    IClient : IClient := FBRedis;
    IRedisHelpers : IHelpers := FbRedis;
    sKey, sValue, sData : STRING(gcMAX_STRINGLENGHT);
    xSuccess : bool;
    eStatusCode : eStatusCode;
    typOptions : typSetOptions;
END_VAR
```

```
IRedisHelpers.BlockingMode := TRUE; 

sKey := 'lux';
sValue := '2000';

// SET 
eStatusCode := IClient.Set(psKey:= ADR(sKey), psValue:= ADR(sValue), ptypOptions:= ADR(typOptions), sRetVal:= sData);

// GET
eStatusCode := IClient.Get(psKey:= ADR(sKey), sRetVal:= sData);

// Test
if sData = sValue then
    xSuccess := true;
end_if

```

## Note

Make sure you set the timeoutvalue correctly. This may need some tuning depending on your system.
The blocking propterty will halt the program execution and increase cycle time.
propterty