---
description: Method
---

# XADD

## Codesys usage

Appends the specified stream entry to the stream at the specified key:

```
VAR	
    RedisCient : FbRedis;
    RedisStream : IStream := RedisCient;
    xConnected, xStreamXAdd: BOOL;
    sIP : STRING; 
    wDefaultPort : WORD := 6379;
    sKey, sResult : STRING(gcMAX_STRINGLENGHT);
    asfield, asValue : ARRAY [1..gcMAX_ELEMENT] OF STRING(gcMAX_STRINGLENGHT);
    typEntryId : typEntryId;
    TypStreamOpt :TypStreamOptions;
END_VAR
```

```
xConnected := RedisStream.Connect(sServer:= sIP, wPortNo:= wDefaultPort, xUnix:=FALSE);
IF xConnected THEN
    IF xStreamXAdd THEN
        sResult := RedisStream.XAdd(psKey:= ADR(sKey), typEntryId:= typEntryId, asField:= asfield,	asValue:= asValue, pTypStreamOpt:= ADR(TypStreamOpt));
        IF sResult <> '' THEN
            xStreamXAdd := FALSE;
        END_IF	
    END_IF
END_IF
```