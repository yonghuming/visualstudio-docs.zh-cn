---
title: "IMachineDebugManager::RemoveApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IMachineDebugManager.RemoveApplication
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IMachineDebugManager::RemoveApplication"
ms.assetid: 873509ce-e638-484a-b2a2-489a8ce7dbfe
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManager::RemoveApplication
从运行的应用程序中移除应用程序列表中。  
  
## 语法  
  
```  
HRESULT RemoveApplication(  
   DWORD  dwAppCookie  
);  
```  
  
#### 参数  
 `dwAppCookie`  
 \[out\]提供的cookie，当应用程序添加到应用程序列表中。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法由进程调用调试管理器，只要 `IProcessDebugManager::RemoveApplication` 调用。  
  
## 请参阅  
 [IMachineDebugManager::AddApplication](../../winscript/reference/imachinedebugmanager-addapplication.md)   
 [IMachineDebugManager 接口](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)