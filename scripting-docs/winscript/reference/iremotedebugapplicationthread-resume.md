---
title: "IRemoteDebugApplicationThread::Resume | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.Resume
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::Resume"
ms.assetid: ac290861-515d-4f06-b452-3b96f54e538c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::Resume
继续执行线程。  
  
## 语法  
  
```  
HRESULT Resume(  
   DWORD*  pdwCount  
);  
```  
  
#### 参数  
 `pdwCount`  
 \[in\]线程的挂起计数。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 当此方法还原线程时，它通过递减挂起计数。  
  
## 请参阅  
 [IRemoteDebugApplicationThread 接口](../../winscript/reference/iremotedebugapplicationthread-interface.md)