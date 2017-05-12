---
title: "IDebugSessionProvider::StartDebugSession | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSessionProvider.StartDebugSession
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugSessionProvider::StartDebugSession"
ms.assetid: 47697dfb-d4e1-492c-a14f-753e28195a76
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSessionProvider::StartDebugSession
启动与指定的应用程序的调试会话。  
  
## 语法  
  
```  
HRESULT StartDebugSession(  
   IRemoteDebugApplication*  pda  
);  
```  
  
#### 参数  
 `pda`  
 \[in\]用于指定调试应用程序。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法开始使用指定的应用程序的调试会话。  调试器应在调用返回 `IRemoteDebugApplication::ConnectDebugger` 从此之前调用。  
  
## 请参阅  
 [IDebugSessionProvider 接口](../../winscript/reference/idebugsessionprovider-interface.md)   
 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)