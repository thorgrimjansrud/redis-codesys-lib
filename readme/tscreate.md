---
description: Method
---

# TSCREATE

## Codesys usage

Create a new time series:

```
VAR	
    FbRedis : FbRedis;
    IRedis : ITimeseries := FbRedis;
    xTrigger : BOOL;
    sResult, sKey : STRING;
    typTsOptions : typSetOptions;
END_VAR
```

```
IF xConnected then
    IF xTrigger THEN	
        sResult := IRedis.TsCreate(psKey:= ADR(sKey), ptypTsOptions:= ADR(typTsOptions));
        IF sResult <> '' THEN
            xTrigger := FALSE;
        END_IF
    END_IF	
END_IF 	 
```