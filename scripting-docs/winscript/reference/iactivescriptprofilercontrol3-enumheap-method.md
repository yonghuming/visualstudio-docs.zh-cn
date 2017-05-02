---
title: "IActiveScriptProfilerControl3::EnumHeap 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 2799d06d-20dd-4c12-9646-554c0ea3606e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IActiveScriptProfilerControl3::EnumHeap 方法
返回可以用于循环访问GC堆对象在关联的脚本引擎中的接口\([IActiveScriptProfilerHeapEnum 接口](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)\)。  
  
 可以调用此方法在调试或发布模式。  此方法，当用户界面线程空闲时，应调用。  在调用方法之后，不应执行操作\( [IActiveScriptProfilerHeapEnum::Next 方法](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) 的脚本引擎，直到 [IActiveScriptProfilerHeapEnum::Next 方法](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) 返回S\_FALSE或释放 [IActiveScriptProfilerHeapEnum 接口](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) 接口指针。  
  
## 语法  
  
```  
HRESULT EnumHeap([out] IActiveScriptProfilerHeapEnum** ppEnum);  
  
```  
  
#### 参数  
 ppEnum  
 \[out\] 返回 [IActiveScriptProfilerHeapEnum 接口](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)。  
  
## 返回值  
 此 HRESULT。