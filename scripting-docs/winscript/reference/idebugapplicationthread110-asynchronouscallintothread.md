---
title: "IDebugApplicationThread110::AsynchronousCallIntoThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 06b3031a-4aec-4a47-afaa-04642a4c4870
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# IDebugApplicationThread110::AsynchronousCallIntoThread
在主线程进行异步调用。  
  
> [!IMPORTANT]
>  [IDebugApplicationThread110 接口](../../winscript/reference/idebugapplicationthread110-interface.md) 由PDM v11.0实现和更大。  找到在activdbg100.h。  
  
## 语法  
  
```cpp  
HRESULT AsynchronousCallInMainThread([in] IDebugThreadCall* pptc, [in] DWORD_PTR dwParam1, [in] DWORD_PTR dwParam2, [in] DWORD_PTR dwParam3);  
  
```  
  
#### 参数  
 `pptc`  
 调用的 [IDebugThreadCall 接口](../../winscript/reference/idebugthreadcall-interface.md) 对象。  
  
 `dwParam1`  
 调用第一个参数。  
  
 `dwParam1`  
 调用第一个参数。  
  
 `dwParam2`  
 调用第二个参数。  
  
 `dwParam3`  
 调用第三个参数。  
  
## 请参阅  
 [IDebugApplication110 接口](../../winscript/reference/idebugapplication110-interface.md)