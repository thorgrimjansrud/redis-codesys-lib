---
description: Method
---

# XREAD

## Codesys usage

Read data from one or multiple streams:

```
VAR	
    FbRedis : FbRedis;
    IRedis : IStream := FbRedis;
    xConnected, xXRead: BOOL;
    asKey : ARRAY [1..gcMAX_STREAMS] OF STRING(gcMAX_STRINGLENGHT);
    uiCountMax : UINT;
    atypEntryId : ARRAY [1..gcMAX_ELEMENT] OF typEntryId;
    atypStreamResult : ARRAY [1..gcMAX_STREAMS] OF typStreamResult;
END_VAR
```

```
IF xConnected THEN
    // Note! Block not supported, and Id's are set to 0-0.
    atypStreamResult := IRedis.XRead(asKey:= asKey, uiCount:= uiCountMax, atypEntryId:= atypEntryId, xTrigger:= xXRead);
END_IF
```

## Note

The typEntry is the ID if the stream specified either as 1) sEntryId or 2) uliTime_ms and uliSequence (1 and 2 can not be combined).