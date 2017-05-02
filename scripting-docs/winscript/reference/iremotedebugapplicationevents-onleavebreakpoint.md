---
title: "IRemoteDebugApplicationEvents::OnLeaveBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEvents.OnLeaveBreakPoint
apilocation: jscript.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEvents::OnLeaveBreakPoint"
ms.assetid: 00449a23-1f67-4078-ad06-4c426abf7587
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplicationEvents::OnLeaveBreakPoint
处理保留的断点一个事件。  
  
## 语法  
  
```  
HRESULT OnLeaveBreakPoint(  
   IRemoteDebugApplicationThread*  prdat  
);  
```  
  
#### 参数  
 `prdat`  
 \[in\]出断点的应用程序线程。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法处理保留的断点一个事件。  
  
## 请参阅  
 [IRemoteDebugApplicationEvents 接口](../../winscript/reference/iremotedebugapplicationevents-interface.md)