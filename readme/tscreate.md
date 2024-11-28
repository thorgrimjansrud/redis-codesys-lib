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
    xConnected, xTrigger, xUnix: BOOL;
    wDefaultPort : WORD := 6379;
    sResult, sKey, sIP : STRING;
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