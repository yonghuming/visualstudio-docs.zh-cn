---
title: "IRemoteDebugApplicationEvents::OnCreateThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEvents.OnCreateThread
apilocation: jscript.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEvents::OnCreateThread"
ms.assetid: 0b7c5181-eda6-4303-b4ae-d45962e8a3d3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationEvents::OnCreateThread
处理创建线程活动。  
  
## 语法  
  
```  
HRESULT OnCreateThread(  
   IRemoteDebugApplicationThread*  prdat  
);  
```  
  
#### 参数  
 `prdat`  
 \[in\]新创建的线程。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法负责创建线程活动。  
  
## 请参阅  
 [IRemoteDebugApplicationEvents 接口](../../winscript/reference/iremotedebugapplicationevents-interface.md)