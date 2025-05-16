---
description: Method
---

# CONNECT

## Codesys usage

Connect to a remote Redis server at given IP or unix socket:

```
VAR	
	FbRedis : FbRedis;
	IRedisBase : IBase := FbRedis;
	typConnectStatus : typConnectStatus;
	sHost : STRING; 
	wDefaultPort : WORD := 6379;
END_VAR
```
```
typConnectStatus := IRedisBase.connect(sHost:= sHost, wPortNo:= wDefaultPort);
IF typConnectStatus.xConnected THEN	
  ...	
END_IF
```

## Note

After each reset (soft and hard) and download of program Codesys will create a new socket descriptor (socket file descriptor is not retained in Codesys).
A multiple of socket descriptors can thus be excisting in the system/OS.  
