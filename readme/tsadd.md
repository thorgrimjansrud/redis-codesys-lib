---
description: Method
---

# TSADD

## Codesys usage

Appends the specified stream entry to the stream at the specified key:

```
VAR	
    FbRedis: FbRedis;
    IRedis: ITimeseries := FbRedis;
    xConnected, xTrigger: BOOL;
    sKey, sValue, sResult : STRING(gcMAX_STRINGLENGHT);
    typTimestamp : typTimestamp;
    typTsOptions : typTsOptions;
END_VAR
```

```
IF xConnected THEN
    IF xTrigger THEN
        sResult := IRedis.TsAdd(psKey:= ADR(sKey), pTyptimestamp:= ADR(typTimestamp), psValue:= ADR(sValue), ptypTsOptions:= ADR(typTsOptions));
        IF sResult <> '' THEN
            xTrigger := FALSE;
        END_IF	
    END_IF
END_IF	 
```