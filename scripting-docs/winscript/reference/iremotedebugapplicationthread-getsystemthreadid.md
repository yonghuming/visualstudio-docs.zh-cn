---
title: "IRemoteDebugApplicationThread::GetSystemThreadId | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.GetSystemThreadId
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::GetSystemThreadId"
ms.assetid: 6a6d5f62-4f60-4e87-9206-3c6f2e026d11
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::GetSystemThreadId
返回一个运行系统依赖的标识符与线程关联。  
  
## 语法  
  
```  
HRESULT GetSystemThreadId(  
   DWORD*  dwThreadId  
);  
```  
  
#### 参数  
 `dwThreadId`  
 \[in\]一个运行系统依赖的标识符与线程关联。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 `dwThreadId` 的值不需要是唯一的。设备上。  
  
## 请参阅  
 [IRemoteDebugApplicationThread 接口](../../winscript/reference/iremotedebugapplicationthread-interface.md)