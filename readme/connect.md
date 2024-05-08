---
description: Method
---

# CONNECT

## Codesys usage

The CONNECT method will connect to a remote Redis server at given IP or unix socket:

```
VAR	
	RedisClient : FbRedis;
	Redis : IClient := RedisClient;
END_VAR
```

<pre><code><strong>xConnected := Redis.connect(sServer:= '127.0.0.1', wPortNo:= 6379, xUnix:=false);
</strong>IF xConnected THEN	
  ...	
END_IF
</code></pre>
