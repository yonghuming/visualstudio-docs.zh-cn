---
title: "IMachineDebugManagerCookie::AddApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IMachineDebugManagerCookie.AddApplication
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IMachineDebugManagerCookie::AddApplication"
ms.assetid: 4d5503c5-aca9-4cf7-9900-f77bf5f3263d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManagerCookie::AddApplication
添加一个应用程序向运行的应用程序列表中。  
  
## 语法  
  
```  
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwDebugAppCookie,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### 参数  
 `pda`  
 \[out\]一个指向运行的应用程序的应用程序列表中。  
  
 `dwDebugAppCookie`  
 \[in\]标识调试应用程序的cookie。  
  
 `pdwAppCookie`  
 \[in\]使用从计算机移除应用程序中使用cookie调试管理器。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法由进程调用调试管理器，只要 `IProcessDebugManager::AddApplication` 调用。  
  
## 请参阅  
 [IMachineDebugManagerCookie 接口](../../winscript/reference/imachinedebugmanagercookie-interface.md)   
 [IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)