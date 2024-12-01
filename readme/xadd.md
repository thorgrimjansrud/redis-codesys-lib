---
description: Method
---

# XADD

## Codesys usage

Appends the specified stream entry to the stream at the specified key:

```
VAR	
    FbRedis : FbRedis;
    IRedis : IStream := FbRedis;
    xConnected, xStreamXAdd: BOOL;
    sKey, sResult : STRING(gcMAX_STRINGLENGHT);
    asfield, asValue : ARRAY [1..gcMAX_ELEMENT] OF STRING(gcMAX_STRINGLENGHT);
    typEntryId : typEntryId;
    TypStreamOpt :TypStreamOptions;
END_VAR
```

```

IF xConnected THEN
    sResult := IRedis.XAdd(psKey:= ADR(sKey), xAutoGenId:= xAutoGenId, typEntryId:= typEntryId, asField:= asField, asValue:= asValue, pTypStreamOpt:= ADR(TypStreamOpt), xTrigger:= xTrigger);
    if sResult <> '' then
        // do something
    END_IF
END_IF
```

## Note

The typEntry is the ID if the stream specified either as 1) sEntryId or 2) uliTime_ms and uliSequence (1 and 2 can not be combined).