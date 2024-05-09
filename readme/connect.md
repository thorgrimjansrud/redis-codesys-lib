---
description: Method
---

# CONNECT

## Codesys usage

Connect to a remote Redis server at given IP or unix socket:

```
VAR	
	RedisClient : FbRedis;
	Redis : IClient := RedisClient;
	xConnected : BOOL;
	sIP : STRING; 
	wDefaultPort : WORD := 6379;
END_VAR
```
```
xConnected := Redis.connect(sServer:= sIP, wPortNo:= wDefaultPort, xUnix:=false);
IF xConnected THEN	
  ...	
END_IF
```
