---
title: "IRemoteDebugApplicationThread::Suspend | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.Suspend
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::Suspend"
ms.assetid: fd5cc874-2970-4092-b1cd-e638775b0e20
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::Suspend
挂起线程。  
  
## 语法  
  
```  
HRESULT Suspend(  
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
 当此方法挂起线程时，它会增加挂起计数。  
  
## 请参阅  
 [IRemoteDebugApplicationThread 接口](../../winscript/reference/iremotedebugapplicationthread-interface.md)