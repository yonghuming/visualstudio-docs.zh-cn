---
title: "IDebugApplicationThread110::IsSuspendedForBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread110::IsSuspendedForBreakPoint"
ms.assetid: 60688222-557f-4a43-a19b-846cee393cd0
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationThread110::IsSuspendedForBreakPoint
确定 [IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) 是否在此线程和尚未完成。  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110 接口](../../winscript/reference/idebugapplicationthread110-interface.md) 由PDM v11.0实现和更大。  找到在activdbg100.h。  
  
## 语法  
  
```cpp  
HRESULT IsSuspendedForBreakPoint([out, annotation("_Out_")] BOOL * pfIsSuspended);  
```  
  
#### 参数  
 `pfIsSuspended`  
 \[out\] `true`，如果线程为断点挂起，否则 `false`。  
  
## 请参阅  
 [IDebugApplicationThread110 接口](../../winscript/reference/idebugapplicationthread110-interface.md)