---
description: Method
---

# HGETALL

## Codesys usage

Reads all fields and values stored at hash:

```
VAR
  RedisClient : FbRedis;
  Redis : IClient := RedisClient;
  xConnected: BOOL;
  sKey : STRING;
END_VAR
```

```
xConnected := RedisStream.Connect(sServer:= sIP, wPortNo:= wDefaultPort, xUnix:=FALSE);
IF xConnected THEN
	atypElements := Redis.HgetAll(psKey:= ADR(sKey));
END_IF
```

Or if we want several keys, something like:

```
VAR
	RedisClient : FbRedis;
	Redis : IClient := RedisClient;
	xConnected: BOOL;
	sKey1: string;
	sKey2: string;
	xTrigger: BOOL;
	bGetAmountCnt: INT := 1;
END_VAR
```

```
IF xTrigger THEN
	IF bGetAmountCnt = 1 THEN
		sKey := 'sKey1';
		atypElementsModule1 := IRedis.HgetAll(psKey:= ADR(sKey1));
		IF sKey1 = '' THEN
			RETURN;
		ELSE
			bGetAmountCnt := bGetAmountCnt + 1;
		END_IF
	END_IF
	
	IF bGetAmountCnt = 2 THEN
		sKey := 'sKey2';
		atypElementsModule2 := IRedis.HgetAll(psKey:= ADR(sKey2));
		IF sKey2 = '' THEN
			RETURN;
		ELSE
			bGetAmountCnt := 0;
			xTrigger := false;
		END_IF
	END_IF
END_IF
```
