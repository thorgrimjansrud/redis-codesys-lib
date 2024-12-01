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
    xConnected, xTrigger, xUnix: BOOL;
    sKey, sValue, sResult : STRING(gcMAX_STRINGLENGHT);
    typTimestamp : typTimestamp;
    typTsOptions : typTsOptions;
END_VAR
```

```
IF xConnected THEN
    IF xTrigger THEN
        sResult := IRedis.XAdd(psKey:= ADR(sKey), typEntryId:= typEntryId, asField:= ADR(asfield),	asValue:= ADR(asValue), pTypStreamOpt:= ADR(TypStreamOpt));
        IF sResult <> '' THEN
            xTrigger := FALSE;
        END_IF	
    END_IF
END_IF	 
```