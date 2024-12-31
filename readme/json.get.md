---
description: Method
---

# JSON.GET

RedisJSON must be installed.

## Codesys usage

Return the value at path in JSON serialized form:

```
VAR
    FbRedis : FbRedis;
    IRedis : IJson := FbRedis;
    xTrigger, xNX, xXX : BOOL;
    sKey, sRootPath : STRING;
    sValue : STRING(gcMAX_STRINGLENGHT);
END_VAR
```

```
IF xTrigger THEN
    psRetValue := IRedis.JsonGet(psKey:= ADR(sKey), psPath:= ADR(sPath), xIndent:= xIndent, xNewLine:= xNewLine, xSpace:= xSpace);
    IF psRetValue^ <> '' THEN
        xReadJson := FALSE;
    END_IF
END_IF 
```

## Note sRootPath

When a dollar sign '$' is in a string literal, the following two characters are interpreted as a hexadecimal code according to the coding in ISO/IEC 8859-1. This means $n$r is new line and linebreak. Two dollar '$$' is a dollar '$'.