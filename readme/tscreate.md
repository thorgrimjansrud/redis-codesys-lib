---
description: Method
---

# TSCREATE

## Codesys usage

Create a new time series:

```
VAR	
    RedisClient : FbRedis;
    Redis : ITimeseries := RedisClient;
    xTrigger : BOOL;
    sResult, sKey : STRING;
    typTsOptions : typSetOptions;
END_VAR
```

```
IF xTrigger THEN	
    sResult := ITimeseries.TsCreate(psKey:= ADR(sKey), ptypTsOptions:= ADR(typTsOptions));
    IF sResult <> '' THEN
        xTrigger := FALSE;
    END_IF
END_IF	 	 
```