---
description: Method
---

# TSCREATE

## Codesys usage

Create a new time series:

```
VAR	
    RedisClient : FbRedis;
    IRedisBase: IBase := Redis;
    Redis : ITimeseries := RedisClient;
    xConnected, xTrigger, xUnix: BOOL;
    wDefaultPort : WORD := 6379;
    sResult, sKey, sIP : STRING;
    typTsOptions : typSetOptions;
END_VAR
```

```
xConnected := IRedisBase.Connect(sServer:= sIP, wPortNo:= wDefaultPort, xUnix:= xUnix);

IF xConnected then
    IF xTrigger THEN	
        sResult := ITimeseries.TsCreate(psKey:= ADR(sKey), ptypTsOptions:= ADR(typTsOptions));
        IF sResult <> '' THEN
            xTrigger := FALSE;
        END_IF
    END_IF	
END_IF 	 
```