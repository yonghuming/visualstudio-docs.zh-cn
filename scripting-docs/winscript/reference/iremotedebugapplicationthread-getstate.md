---
title: "IRemoteDebugApplicationThread::GetState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationThread.GetState
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationThread::GetState"
ms.assetid: 44503a78-efa9-4fbf-98be-a5dcfa329c5a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationThread::GetState
获取此线程的状态。  
  
## 语法  
  
```  
HRESULT GetState(  
   DWORD*  pState  
);  
```  
  
#### 参数  
 `pState`  
 \[in\]下面的线程状态的组合标记：  
  
|常量|值|说明|  
|--------|-------|--------|  
|THREAD\_STATE\_RUNNING|0x00000001|线程上运行。|  
|THREAD\_STATE\_SUSPENDED|0x00000002|线程被挂起。|  
|THREAD\_BLOCKED|0x00000004|线程已被阻止。|  
|THREAD\_OUT\_OF\_CONTEXT|0x00000008|线程是在内容之外。|  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法获取此线程的状态。  
  
## 请参阅  
 [IRemoteDebugApplicationThread 接口](../../winscript/reference/iremotedebugapplicationthread-interface.md)