---
title: "IDebugSessionProviderEx:StartDebugSession | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSessionProviderEx:StartDebugSession
apilocation: scrobj.dll
ms.assetid: 247337ca-476c-4aa7-8500-d84fd1d98176
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugSessionProviderEx:StartDebugSession
启动与指定的应用程序的调试会话。  
  
## 语法  
  
```  
HRESULT StartDebugSession(  
   IRemoteDebugApplication*  pda  
   BOOL  fQuery  
);  
```  
  
#### 参数  
 `pda`  
 \[in\]用于指定调试应用程序。  
  
 `fQuery`  
 \[in\] True指示一个查询。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法开始使用指定的应用程序的调试会话。  调试器应在调用返回 `IRemoteDebugApplication::ConnectDebugger` 从此之前调用。  
  
## 请参阅  
 [IDebugSessionProviderEx 接口](../../winscript/reference/idebugsessionproviderex-interface.md)   
 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)