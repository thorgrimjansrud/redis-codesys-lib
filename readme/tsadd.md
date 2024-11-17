---
description: Method
---

# TSADD

## Codesys usage

Appends the specified stream entry to the stream at the specified key:

```
VAR	
    Redis: FbRedis;
    IRedisBase: IBase := Redis;
    ITimeseries: ITimeseries := Redis;
    xConnected, xTrigger, xUnix: BOOL;
    wDefaultPort : WORD := 6379;
    sIP : STRING; 
    sKey, sValue, sResult : STRING(gcMAX_STRINGLENGHT);
    typTimestamp : typTimestamp;
    typTsOptions : typTsOptions;
END_VAR
```

```
xConnected := IRedisBase.Connect(sServer:= sIP, wPortNo:= wDefaultPort, xUnix:= xUnix);
IF xConnected THEN
    IF xTrigger THEN
        sResult := ITimeseries.TsAdd(psKey:= ADR(sKey), typEntryId:= typEntryId, asField:= ADR(asfield),	asValue:= ADR(asValue), pTypStreamOpt:= ADR(TypStreamOpt));
        IF sResult <> '' THEN
            xTrigger := FALSE;
        END_IF	
    END_IF
END_IF 	 
```