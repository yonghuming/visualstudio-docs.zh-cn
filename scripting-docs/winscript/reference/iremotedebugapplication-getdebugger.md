---
title: "IRemoteDebugApplication::GetDebugger | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.GetDebugger
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::GetDebugger"
ms.assetid: 3d173b86-9281-4a3c-9550-d79408fd50ba
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::GetDebugger
返回当前调试器连接到应用程序。  
  
## 语法  
  
```  
HRESULT GetDebugger(  
   IApplicationDebugger**  pad  
);  
```  
  
#### 参数  
 `pad`  
 \[in\]当前调试器连接到应用程序。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法返回当前调试器连接到应用程序。  
  
## 请参阅  
 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)   
 [IRemoteDebugApplication 接口](../../winscript/reference/iremotedebugapplication-interface.md)