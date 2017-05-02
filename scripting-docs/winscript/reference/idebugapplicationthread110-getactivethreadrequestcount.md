---
title: "IDebugApplicationThread110::GetActiveThreadRequestCount | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread110::GetActiveThreadRequestCount"
ms.assetid: 025d2072-1d7f-4448-8aa3-38a014313570
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugApplicationThread110::GetActiveThreadRequestCount
返回线程请求数从当前进程的PDM的线程切换framework的。  此值通常为0或1。  但是，该数字可能更高版本中，如果一个线程调用过程的开头，但同步调用线程的触发器，或者挂起线程并允许传入的调用重新处理\(例如，通过触发 [IRemoteDebugApplicationEvents 接口](../../winscript/reference/iremotedebugapplicationevents-interface.md) 事件，在调试器线程问题\)。  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110 接口](../../winscript/reference/idebugapplicationthread110-interface.md) 由PDM v11.0实现和更大。  找到在activdbg100.h。  
  
## 语法  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
  
```  
  
#### 参数  
 `puiThreadRequests`  
 \[in\]线程请求的数目。  
  
## 请参阅  
 [IDebugApplicationThread110 接口](../../winscript/reference/idebugapplicationthread110-interface.md)