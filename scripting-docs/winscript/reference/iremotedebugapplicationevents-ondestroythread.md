---
title: "IRemoteDebugApplicationEvents::OnDestroyThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEvents.OnDestroyThread
apilocation: jscript.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEvents::OnDestroyThread"
ms.assetid: 7c716ccc-7b82-41b2-9a16-d0366999dee8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationEvents::OnDestroyThread
处理一个线程销毁的事件。  
  
## 语法  
  
```  
HRESULT OnDestroyThread(  
   IRemoteDebugApplicationThread*  prdat  
);  
```  
  
#### 参数  
 `prdat`  
 \[in\]销毁的线程。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法处理线程被销毁的事件。  
  
## 请参阅  
 [IRemoteDebugApplicationEvents 接口](../../winscript/reference/iremotedebugapplicationevents-interface.md)