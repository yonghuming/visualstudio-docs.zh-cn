---
title: "IDebugApplicationThread110::IsThreadCallable | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread110::IsThreadCallable"
ms.assetid: 2a75a366-801d-47e0-bba3-51aa669e03a7
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationThread110::IsThreadCallable
确定此线程是否在将处理调用使用PDM的线程切换机制，如SynchronousCallInThread的状态。  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110 接口](../../winscript/reference/idebugapplicationthread110-interface.md) 由PDM v11.0实现和更大。  找到在activdbg100.h。  
  
## 语法  
  
```cpp  
HRESULT IsThreadCallable([out, annotation("_Out_")] BOOL * pfIsCallable);  
```  
  
#### 参数  
 `pfIsCallable`  
 \[out\] `true`，如果线程可调用的，否则 `false`。  
  
## 请参阅  
 [IDebugApplicationThread110 接口](../../winscript/reference/idebugapplicationthread110-interface.md)