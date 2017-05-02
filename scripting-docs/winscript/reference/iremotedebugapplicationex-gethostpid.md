---
title: "IRemoteDebugApplicationEx:GetHostPid | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEx:GetHostPid
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEx:GetHostPid"
ms.assetid: 4cf9f46c-29cf-4201-87f0-5b1ddbed2f2b
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplicationEx:GetHostPid
返回宿主应用程序的进程ID。  
  
## 语法  
  
```  
HRESULT GetHostPid(  
   DWORD*  dwHostPid  
);  
```  
  
#### 参数  
 `dwHostPid`  
 \[in\]宿主进程标识符。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 使用由IDE。  
  
## 请参阅  
 [IRemoteDebugApplicationEx Interface](http://msdn.microsoft.com/zh-cn/2f65fa67-06b7-4053-8945-22383ab66343)