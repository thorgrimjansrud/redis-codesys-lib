### 1.0.0.13
- Issue #38. Description/readme Pub-Sub.
- Issue #35. SET without sKey gives a variable.
- Connect method. Use host path for IP and unix socket.
- Add check for compile and "xIsUnix" not enabled, but unix sockets is used.
- Connect method. Added Socket file descriptor information.
- For .md and Codesys help texts: Changed interface declaration names.
- xRead method: Changed nested IF's to return early.
- xRead method: Changed trigger reset.
- Added error handling enumeration eEthError to TCP connect and TCP send/recieve.
- Renamed statemachine index to "bState".
- Changed some status texts.
- Added status codes to method GetPubSubMsg, LPOP and SubscriberBase. Reset status code on state 0.


### 1.0.0.12
- Changed SubscriberBase method in/out from "xTrigger" to "xAddChannel".
- Naming "xAddChannel" in readme.md for psubscribe and punsubsribe 

### 1.0.0.11
- Bugfix from 1.0.0.10.   
  Functions beside tscreate and tsadd does not work!

### 1.0.0.10 (do not use!)
- Added tscreate and tsadd.
- Changed Connect function (xOpen to xConnect inside)