---
title: "IRemoteDebugApplication::QueryAlive | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.QueryAlive
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::QueryAlive"
ms.assetid: 08e49d3b-6fb3-4438-960e-f05395ba9b17
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::QueryAlive
指示应用程序是否具有响应能力。  
  
## 语法  
  
```  
HRESULT QueryAlive();  
```  
  
#### 参数  
 此方法没有参数。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法指示应用程序是否具有响应能力。  此方法的实现应始终返回 `S_OK`。  
  
 如果应用程序进程意外停止，COM返回从排列的代理的错误为调用此方法。  
  
## 请参阅  
 [IRemoteDebugApplication 接口](../../winscript/reference/iremotedebugapplication-interface.md)