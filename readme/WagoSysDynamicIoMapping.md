---
description: Gateway
---

# Redis IO gateway

## Codesys usage

Dynamic configuration and processing of IO modules. Add the library "WagoSysDynamicIoMapping". Set property "use dynamic memory allocation" for the project.
Example provides a minimalistic, easy-to-understand picture of how to configure the dynamic setup of a digital module. Here we use the REDIS get command to
set a digital output on a Wago 750-508 module:

```
PROGRAM PLC_PRG
VAR
	RedisClient : FbRedis;
	Redis : IClient := RedisClient;
	xConnected, xTrigGet : BOOL;	
	sResult, sKey: STRING; 
	xTerminalManagerReady : BOOL;
	uiIdx: INT;
	uiSize: UINT;
	xInit: BOOL;
	wOutData: WORD;
END_VAR
```
PLC_PRG
```
xConnected := Redis.connect(sServer:= '10.0.0.113', wPortNo:= 6379, xUnix:=FALSE);

IF xConnected THEN	
	PLC_PRG.IoGw();
	sKey := 'module_1_750_508_ch1';
	IF xTrigGet THEN
		sResult := Redis.Get(psKey:= ADR(sKey)); 
		IF sResult <> '' THEN
			IF sResult = 'true' THEN
				wOutData := 1;
			ELSE
				wOutData := 0;
			END_IF
			xTrigGet := FALSE;
		END_IF
	END_IF	 	
END_IF
```
Action IoGw (PLC_PRG)
```
IF NOT xTerminalManagerReady THEN
	xTerminalManagerReady := DynIomanager.DynKbusIoManager.xIsInit; 
	RETURN;
END_IF

IF NOT xInit THEN
	FOR uiIdx := 1 TO DynIomanager.DynKbusIoManager.coModules.uiModuleCount DO
		CASE DynIomanager.DynKbusIoManager.coModules.aIModules[uiIdx].eType OF
			WagoTypesBusServices.eTerminalType.DIGITAL_OUTPUT_DIAG:
			uiSize := DynIomanager.DynKbusIoManager.coModules.aIModules[uiIdx].GetModuleOutputSize();
		END_CASE
	END_FOR
	xInit := TRUE;
END_IF

IF xInit THEN
	FOR uiIdx := 1 TO DynIomanager.DynKbusIoManager.coModules.uiModuleCount DO
		CASE DynIomanager.DynKbusIoManager.coModules.aIModules[uiIdx].eType OF
			WagoTypesBusServices.eTerminalType.DIGITAL_OUTPUT_DIAG:
					DynIoManager.DynKbusIoManager.coModules.aIModules[uiIdx].SetProcessOutData(pOutData:= ADR(wOutData), uiNOutData:= uiSize);
		END_CASE
	END_FOR
END_IF
```

