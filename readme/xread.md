---
description: Method
---

# XREAD

## Codesys usage

Read data from one or multiple streams:

```
VAR	
    RedisCient : FbRedis;
    RedisStream : IStream := RedisCient;
    xConnected, xXRead: BOOL;
    sIP : STRING; 
    wDefaultPort : WORD := 6379;
    asKey : ARRAY [1..gcMAX_STREAMS] OF STRING(gcMAX_STRINGLENGHT);
    uiCountMax : UINT;
    atypEntryId : ARRAY [1..gcMAX_ELEMENT] OF typEntryId;
    atypStreamResult : ARRAY [1..gcMAX_STREAMS] OF typStreamResult;
END_VAR
```

```
xConnected := RedisStream.Connect(sServer:= sIP, wPortNo:= wDefaultPort, xUnix:=FALSE);
IF xConnected THEN
    // Note! Block not supported, and Id's are set to 0-0.
    atypStreamResult := RedisStream.XRead(asKey:= asKey, uiCount:= uiCountMax, atypEntryId:= atypEntryId, xTrigger:= xXRead);
END_IF
```